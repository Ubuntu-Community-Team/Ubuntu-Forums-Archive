---
title: "An interesting Question (A Doul UP computer.)"
date: 2007-12-26
forum: General Help
---

### Post by Ioky on 2007-12-26
Imagine you have two computer, and some how you want to do something about them, and make them work as one. (sound pretty cool)

But what can you really do? This question pop to my head, when I get my new IBM computer. I mean now I have two super computer, but then I only have one desk, and one set of keyboard and mouse, with one monitor. Well, you mean ask, why I even get it at the first place. my answer will be because it is $700 off. and I get a duo 2 core IBM computer for like $320. I know it sound stupid, but because of that I think I should do something smart to it, so I wouldn't feel as stupid as I already am. 

I have a few idea, but I don't know which one will actually work, sense I never have two computer to run as one before, I have no idea. I was thinking to connect the two computer with USB or Firewire. and if it is possible, I would like to operate them with one set of key board and mouse, I mean it will be good if both the OS are able to display my Monitor. or even if it can't, my monitor are able to connect to two computer output, so that is not a huge problem.

so yeah, haha, what you do think? (just go wild, I mean any idea can be a billion idea for the future computer) Thing such as operation two difference OS with one set of input and output drives at the same time sound cool to me, so you can have playing game in windows, while, some serious programming are going on in your linux OS, Or maybe you have one computer use as a super firewall system to give super protect to your Main system.  There is just so many possible. out there. 

So tell me what you think.

---

### Post by p_quarles on 2007-12-26
Well, I certainly wouldn't advise you to use USB or Firewire. The fastest way of connecting the two computers would be to use a Gigabit ethernet link. 

Anyway, there are two main ways to do this.

First, and most complicated (and probably pointless if this is a home computer) is to set up a Beowulf cluster. This would essentially allow the two machines to act as one.

Second, much easier and more common, is simply to create a headless server out of one of the machines. You would essentially run one of the computers without any peripherals, and control it via an SSH connection.

---

### Post by Ioky on 2007-12-27
Thanks for you reply so now I need to get two card for both of my computer in order to use gigabit, and I have one question, can I use internet with both computer with only one computer are really connect to the network? I mean it sound pretty cool to use Linux itself as a firewall, so my Windows computer would be much saver. haha,  I am really new to this, and i wonder like to know more about this kind of thing. hehe Thanks all of you who help me on this and read my post.

Maybe, don't let me got too far. OK here is my goal for now.

be able to connect both computer, 
by using one set of input and output drives to operating both the system,
be able to share any file and data between the two computer with a difference OS. (Windows Xp and Ubuntu as I have)

Ideal! if I can connect to the internet with just my Linux computer, and use internet with Win Xp through my linux system, so the linux system can act like a firewall for my window system. 

Sorry, if I have got too far, and too fantasy in my own dream, haha but it sound really cool.

---

### Post by p_quarles on 2007-12-27
> **Ioky said:**
> Thanks for you reply so now I need to get two card for both of my computer in order to use gigabit, and I have one question, can I use internet with both computer with only one computer are really connect to the network? I mean it sound pretty cool to use Linux itself as a firewall, so my Windows computer would be much saver. haha,  I am really new to this, and i wonder like to know more about this kind of thing. hehe Thanks all of you who help me on this and read my post.
You'll need a router (if you don't have one already), but yes, you can certainly connect both computers to the internet.

---

### Post by dagnabit dang doohickey on 2007-12-27
You can also get a cheap KVM switch so you can use both computers with one monitor/keyboard setup.

---

### Post by Ioky on 2007-12-27
so can I just add one gigabit card to each computer which make both my computer have two networking plug, and use one of them for internet, and the other one for connect the to the other computer? just wondering will this give any problem the the system.

---

### Post by rich.bradshaw on 2007-12-27
To get both on internet and able "speak" to each other, plug them both into a router and then plug router into internet.

Standard routers are 100MBit, you can buy more expensive ones that are a Gigabit, in otherwords 10 times faster.

If you use gigabit, you will likely need to upgrade ethernet cards in the PCs as well.

Once you've done that, you want a beowulf cluster, this means both computers act as one, so you are essentiy adding them together.

Knoppix has a variation that lets you do this, but I can't remember what it's called!

---

### Post by Ioky on 2007-12-27
Yeah, I know, but having a router between two computer that is only 5 inch apart is kind of ........ weird. haha is that ok if I add a gigabit card to only one of my computer, so that computer will have two internet/ethernet plug, one for internet, the other one for transfer data between the computers. I mean I really don't want to use a router, thought I know it is kind of one of those "have to" things. i mean I am fine to use othere things like USB or firewire, but I just don't want to use a router
haha. again thanks for your help. I learn a lot

---

### Post by p_quarles on 2007-12-27
Using a router to connect two nearby computers isn't weird at all. In fact, I'd say it's much more efficient than what you're proposing to do (two NICs on each computer). IMHO, *that* would be weird. :D

Also, I mentioned Gigabit ethernet because it's the fastest networking technology available to the average home consumer -- not because it's the only solution. A standard 100 megabit ethernet connection is quite a bit faster than the average internet connection, and will serve most people's needs just fine. I wouldn't splurge on the superfast connection unless you have a specific reason to do so. 

As rich.bradshaw mentioned, there is a variant of Knoppix that will allow you to setup a Beowulf cluster. It's called -- oddly enough -- ClusterKnoppix:
[http://clusterknoppix.sw.be/](http://clusterknoppix.sw.be/)

---

### Post by Ioky on 2007-12-27
ah... I see

---

