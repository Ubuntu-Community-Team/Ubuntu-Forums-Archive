---
title: "Recommendations for an Ubuntu dev laptop"
date: 2017-01-09
forum: General Help
---

### Post by Eugene_Bondarenko on 2017-01-09
Hi,

I've been looking into buying a laptop for messing with web development and docker and wanted to ask for some recommendations. I am looking for a machine with 16gb memory, an SSD and one that supports Linux (or Linux-like) OS smoothly. The options I've considered are:

- Dell XPS 15. Seems to go for $1699. Doesn't come natively with Ubuntu but it *seems* like people have been using Ubuntu on it without too much pain.
- Dell XPS 13. A bit more expensive, goes for $1799. All of the above and comes with native Ubuntu. Smaller display but perhaps it's not that big of a problem. If this laptop and Ubuntu support external large displays smoothly, it might be ok because realistically I'll be doing dev in places where I can plug into external monitor. And when I do have to work on metro, it might actually be better than a 15" display because I've noticed that my current work 15" MBP is a bit too bulky when used on public transit or plane.
- ASUS ZenBook Pro UX501VW. Have been considering this one. Seems like a nice laptop $1499 but then I did some reading and noticed that people have had a lot of pain with newer Ubuntu distros. If it's the case, it's probably not an option.
- New MBP 15". Pretty expensive at $2399. Has OS that should work smoothly but I am not sure if it's worth the extra premium in price? Also everyone around me have been very unhappy about their latest update but I haven't looked into it too much so not sure if it has any deal breakers. 
- Anything I've missed?
- Anything upcoming in the near future that is worth waiting for?

Thanks!

---

### Post by TheFu on 2017-01-09
Get the Dell 13 XPS. No question. 1080p is less than $900 in that model. If you can do without the touch screen, the 4K display version isn't $1800. If it wasn't my money, I'd get one of these things.

If you don't do Android or Java development, any RAM over 8G is overkill.  You'll be able to run about 30 containers in 8G RAM, easily.  I've run 10 full VMs in less than 8G of RAM.  This isn't Windows.

My 15in i5 Dell hasn't left the house in years.  Much prefer the 13in, 1080p, 3lb, 10+ hr battery, core i3 chromebook (running Ubuntu). It only has 4G of RAM, but that is plenty, see:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.8G        1.9G        282M        170M        1.6G        1.4G
Swap:          3.9G         56K        3.9G

``` Currently have 11 windows open, but most are onto other systems on the network.  For me, doing web-app development, the network **IS** the computer. Just don't need portable power.  A cheap laptop and $500 desktop can do amazing things.
For your consideration: [http://www.techspot.com/review/1155-affordable-dual-xeon-pc/](http://www.techspot.com/review/1155-affordable-dual-xeon-pc/)
I'm looking at replacing 4 other systems with 1 of those.  24K passmarks is nothing to sneeze at for $500. No laptop can compare, at any price. 

Pair the desktop/monster with a cheap and light laptop and you get a few nice things.  Redundancy.  Client/Server.  Ability to run 100 VMs or 1,000 containers. Light, portable, display for around the house or from the other side of the world. Critical data doesn't need to leave the house/office. If the $300 laptop gets stolen/lost, it isn't the end of the world.  Having a "private cloud" is nice for people like us.  BTW, for most people just wanting to run 5 VMs, a $150 "server" can easily cover that.  Using a $50 G3258 CPU here, which tests as faster than a 1st generation Core i5.  Transcoding video is slow on it, hence the need for a "monster" system. ;)

---

### Post by chris354 on 2017-01-09
I picked up a £40 desktop tower (acer ax3300) and installed my web server onto that and run Ethernet directly into the router. No need for any peripherals at all once you have installed the OS and ssh server you can fully configure and manage it via the terminal. 

To set mine up i just stood it on my desk and borrowed the peripherals from my main computer. I know this isnt what you asked for but it seems to me that hosting the dev sites on your laptop is taking up resources that honestly would be better used for other things and when you can pick up a perfectly good "server" at such a low price, well you might as well.

---

### Post by Eugene_Bondarenko on 2017-01-13
Hey, just wanted to say thanks for all the thoughts and suggestions. So far I am leaning towards Dell XPS 13, will probably contemplate a bit more, decide on the amount of memory and grab it. 
SSH-ing into instance is a good option but I'd love to have offline access to my dev environment, so that I can do stuff when I am on the train or flying.

---

### Post by TheFu on 2017-01-13
I'm doing some web-app devel today on my 13" chromebook, disconnected.  Just depends on how heavy your dev env is.

I also do devops stuff from it via ssh, but that stuff runs on my normal desktop. Ansible rocks completely.  It could easily be used to run devops from, but I prefer not having access to all those systems from a portable device. Just doesn't make security sense to me. Others might have different needs, of course.

---

### Post by Olav on 2017-01-13
For what it is worth, I would always choose a ~15" laptop. Anything smaller I just find too uncomfortable to use. A larger one, obviously, is impractical to carry around.

I like having a near fullsize keyboard (for touch typing) and not having to hunch over the computer in order to read the tiny letters that are a result of high resolutions on small screens. Yes I know you can change font sizes in most applications, but still. If you are young and still have perfect eyesight you may disregard this advice. Just wait until you reach an age where you may need reading glasses sometimes...

Also I use the laptop as a quick presentation tool sometimes. So if I set it in front of a few people to show them something, it's nice when they can all have a proper view.

I don't care for touchscreens. Had a laptop computer with touchscreen on loan for two weeks but never even used the touchy thing. Still using an old wired mouse that survived 3 different laptops already. I guess I am just used to it.

It's true that RAM > 8 GB is not always necessary. But if you are running a full server stack on your laptop plus several virtual machines plus, say, Eclipse loaded with plugins, it can't hurt either. Storing most of your work on a server under your control is a good idea. Laptops can and sometimes do get lost / stolen etc.

In my home office / study I use a desktop (midi tower) computer with three monitors. The laptop never leaves the bag when I am home.

---

### Post by QIII on 2017-01-13
For a long time I was doing web development on an Odroid XU4.

My opinion is this:  develop on a machine with the lowest reasonable specifications that your product might be used on.  That encourages you to pay a great deal of attention to making your code as streamlined and efficient as possible.

So, for development I might choose an inexpensive used machine a few years old.  Not perfectly state of the art.

---

### Post by TheFu on 2017-01-13
Eclipse - there's the problem. ;)  I don't use an IDE.  Give me 5 xterms (vim, make, debug, manpages, extra stuff ... ) over that any day. 
The OS **is** the IDE. No need for a monster, slow, memory sucking, IDE ... er ... unless you do java. Then you need dual Xeons + 32G of RAM. ;)

BTW, I carried heavy 15inch laptops for 20 yrs around the world a few times. Never again.  Less than 3 lbs. 13inches. 1080p.  We aren't all the same and there are valid reasons for many different types, sizes, weights, of laptops.  Just providing options here.  And that Dell is a beautiful machine. ;)

You'll find what works for you, I'm certain.

---

### Post by ik-0 on 2017-01-14
I've been using the Dell XPS 15 9550 (4K + i7-7600 + 16GB DDR4 + 512GB NVmE SSD) with Ubuntu 14.04 (work image) without issue.  I use it for devops and SW dev, and it works well.  Battery life is approximately 6 to 8 hours with low brightness, wifi, and sw dev.

---

