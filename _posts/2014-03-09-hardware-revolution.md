---
layout: post
description: Hardware could be the new software.
title: The hardware revolution
hn: https://news.ycombinator.com/item?id=7372634
---
It's a pretty great time to be a software engineer. Sure you get great pay and perks, but my favorite part of this vocation is how stupidly easy and cheap it is to try out new ideas. Developers have no shortage of libraries, frameworks, and tools that make it incredibly easy to quickly throw things together into a functional prototype.

I don't think many would dispute that software is a lucrative and amazing field to be in these days, but I have a hunch that something new is coming. Recently I've noticed the same sort of cheap and easy development cycle becoming widely available on the hardware front. First there was the Arduino, which allowed anyone to jumble together a circuit with a few sensors, motors, and lights and have a working prototype. Then came the Raspberry Pi, which gave you a fully capable credit card-sized linux computer for $35. Now we're seeing things like $99 "supercomputers" (the 16-core [Parallella](http://www.parallella.org)) and a $60 quad-core computer (the [ODROID U3](http://hardkernel.com/main/products/prdt_info.php)). These are serious pieces of hardware being sold at some insanely low prices.

We have the recent boom in mobile computing to thank for the rise of these tiny and cheap computers. Competition between companies like Apple, Samsung, and Broadcom has been driving down the cost of ARM processors for mobile devices while simultaneously increasing their performance to be near-desktop levels. The Raspberry Pi, Paralella, and ODROID are all side-effects of the intense competition happening in the mobile sector. Ultimately, hardware hobbyists are the winners here as it's never been cheaper to get a high powered, network ready microprocessor into projects. Plus, since these are fully functional linux computers, you no longer have to write your project's software in low-level languages like C or C++. You can have full control over GPIO (general purpose in/out) pins using languages like Python or Ruby.

The ability to write code for embedded systems using interpreted languages is a major development. These cheap processors are only as useful as the software that runs them, and reducing the amount of complexity required to write good software for hardware projects is a big win for everyone. The Arduino is a fantastic piece of hardware, but do you know how difficult it is to write network-enabled software for it? [Here's](http://arduino.cc/en/Tutorial/WebClient?action=sourceblock&num=1) the code required to make an HTTP request to Google. Compare that to Python's wonderful [requests library](http://docs.python-requests.org/en/latest/). If you had an idea for a web-api based hardware project, what would you rather write it in?

![The ODROID-U3]({{site.url}}/photos/BfCvW1j.jpg)
<div class="caption">This is a 1.7GHz quad-core processor with 2GB of RAM, a network port, 3 USB ports, and HDMI out for $60... This sort of hardware would cost thousands of dollars 15 years ago.</div>

So far we've seen that the cost of hardware is going down and that it's easier to write software for this new hardware. A problem that remains is the steep learning curve of building circuits and complex devices. The good news is hardware education is a field that is also rapidly improving. Companies like [Adafruit](http://adafruit.com) and [Sparkfun](http://sparkfun.com) have realized that education is in their best interest. They've turned their hardware catalogs into [tutorial](http://learn.adafruit.com) [websites](https://learn.sparkfun.com) for aspiring hobbyists to use their parts in order to create amazing things (**shameless side note** - if anyone from Adafruit or Sparkfun is reading this, get in touch, I'd love to work for you guys). Want to learn about the different types of motors you can put in your projects? [There's a tutorial for that](https://learn.sparkfun.com/tutorials/motors-and-selecting-the-right-one). Want to make a device that assists in cocktail mixing? [Yep, there's one for that too](http://learn.adafruit.com/smart-cocktail-shaker).

Hardware education is now monetarily incentivized and because of this, it's getting good. Really good. At the same time we have these tiny, network-enabled linux computers becoming cheap, powerful, widely available, and controlled by high level, high productivity languages. This is a recipe for an amazing future for us hackers. Remember how jQuery, Rails, Django, Bootstrap and tons of tutorials made web-development and rapid prototyping incredibly easy for us? That's exactly what's happening for hardware, and I think the result is going to be even more amazing than what we've created on the web.

{% highlight python linenos %}
import Rpi.GPIO as gpio
import requests, time

gpio.setup(18, gpio.OUT)

while(True):
    r = requests.get(API_BASE + "led/18").json()
    if(r["led_on"] == True):
        gpio.output(18, True)
    else:
        gpio.output(18, False)

    time.sleep(5)

{% endhighlight %}

<div class="caption extra_pad">Look ma, I used my Raspberry Pi to set the state of an LED based on a REST API in 13 lines of Python!</div>

Things are definitely looking bright for the hardware side of technology, but I don't want you to get the impression that hardware will be just as easy as software to create. For starters, in order to put any of these cheap computers to good use, you have to first be able to write the software that controls them. While this is getting better now that you can control GPIO pins with interpreted languages, it still requires a decent knowledge of programming. There are also plenty of other obstacles in the way of easy development with hardware. Some of these obstacles may be broken, however there are others which are firmly enforced by nature. For one, hardware will never be as cheap as software to build. Software is virtually "creating something out of nothing." When you start a new project in software there's nothing to buy; you just open a text editor and begin writing code. Hardware requires you to order parts, find an open workspace, have the correct tools (most of which are not free), etc. It's significantly more difficult to do this than downloading a text editor and compiler. In addition, small electronic parts may be cheap on Adafruit and Sparkfun, but shipping is not. It's hard to justify buying a sensor for 95 cents and paying $4 in shipping just to get it to you. You have to buy parts within larger orders in order for it to be reasonably cheap which makes it difficult to start a project on a whim.

There's also the issue of deployment. Software is *incredibly* easy to deploy into production. I can create a web app, put it up on a service like Heroku, and have it instantly scale to an audience of millions in around 10 minutes (if you can, take a second and think about how incredible this is). Hardware is an *entirely* different game. Going from prototype to scaled deployment takes tons of time, money, and work. Sure it takes time, money, and work to scale software properly, but hardware is an entirely different game. You have to design PCBs to replace your breadboards, find sources for the parts you need, get a manufacturer to assemble the parts, etc. and even then you're only scraping the surface of scaling your device. Scaling software is just significantly easier and cheaper.

<hr />

The list of difficulties which separate us from a hardware hobbyist utopia could go on for a while. While some issues like manufacturing may be turned upside-down by inventions like the 3D printer, I'm not sure how the issue of parts, shipping, and tools could be made as easy as it is for software. Then again, I would have never believed that my thousand-dollar Gateway 2000 would be dwarfed by a $35 computer that fit in my pocket a mere 12 years later. We live in a pretty crazy world these days, so I wouldn't be entirely surprised if the challenges preventing simple hardware development/deployment were mostly overcome in the next decade or so.

However even with these challenges in place today, I still think we're headed towards a *very* exciting future. The advent of cheap microcomputers, increased education, and the ability to write high level code on embedded platforms could be the start of a major growth in hardware hacking and startups. I think these improvements will transform the hardware side of technology into a playground of ideas in a similar way that jQuery, Rails, and Bootstrap did for the web.

We've been given new a set of cheap and powerful toys. Let's play with them and change the world.
