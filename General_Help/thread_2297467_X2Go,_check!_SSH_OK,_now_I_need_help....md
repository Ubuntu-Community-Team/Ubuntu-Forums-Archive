---
title: "X2Go, check! SSH? OK, now I need help..."
date: 2015-10-03
forum: General Help
---

### Post by eyeonyouproductions on 2015-10-03
Hello all,
New to Linux here. I've bounced back and forth for years, but installing flavors of Linux and trying to make them usable for me(And by extension, my family) has always been a nightmare best ended before I started. not so with Ubuntu, this is great, and with everyone's help, I have almost everything dialed in and understand how a lot of this works.

After playing around with remote access options for a media server that I am setting up as well, I finally found X2Go, a wonderful option that is far more effective and reliable than using RDP, VNC or something like TeamViewer. Now my only issue is setting it up so that if for some reason the machine is locked up or has been logged out, I can still remote in(Since it has no monitor, I have to move either the computer or a monitor to wherever the other is). I made a change this evening and logged out the user, which left me unable to get back in using X2Go, so I had to do things the long way.

As I understand it, ssh would let me remote in at any pointy in the computer's boot up and login sequence, but I have no idea where to start and even if I'm understanding this correctly. Is there a set of good newb instructions for ssh? I don't want to do anything fancy, but I definitely want to learn how it basically works.

Thanks in advance for any help, it will be greatly appreciated!

---

### Post by QIII on 2015-10-04
Hello!

You might want to start by reading some of the references at the bottom of [this]("https://help.ubuntu.com/community/SSH").

It may be completely incomprehensible to you and I don't expect you to have an "Aha!" moment.  I don't think it would necessarily be wise to think you understand it all and just launch into something where you might make a mess.  But it will probably help you to start understanding what sorts of questions you want to ask.  This is not a "read the manual" answer, but an invitation of get a bit familiar with the terminology and concepts so you can more easily understand any help offered here.

Read through that, jot down some questions and come back.  We'll help you start to make sense of it.

---

### Post by eyeonyouproductions on 2015-10-04
OK, a few things...
One... Wow, ssh does NOT flow nicely onto a page. Hangs me up every time. :-)

Seriously though, I have a real followup. :-)
1. Is there any issue with putting both server an client on the same machine? If I want to remote into the other machine in my house, but also use them in case I need to access the server I was talking about originally?

2. Is there any reason NOT to use the Ubuntu Software Center for installing software if it has it? This one is something I've been wondering about. It doesn't matter as much, since this adding repositories and apt-get thing is actually quite easy to use, but it saves some searching.

3. Port forwarding: I just skimmed the page, but I read about needing to do this through my router, but it just seems like a direct communication from computer to computer. Is the router forwarding only to add an extra layer of security in some way, or is there something else I'm missing?

In the meantime, this link is perfect. If nothing else, it gives me enough to set this up initially, and then play with it as my needs change. Thanks for the tip!

---

### Post by efflandt on 2015-10-04
1. To connect client and server on same computer, simply connect to localhost or 127.0.0.1, assuming that whatever server is listening to any IP on the server and not bound to a specific IP. For example I have run a minecraft server and client on the same computer or can alternately connect to it from another PC on LAN.

2. Ubuntu Software Center works fine for what it has or finding things in general. But sometimes if you are looking for a specific version of something (like video drivers) that can be easier if you install **synaptic** which was used in earlier Ubuntu versions. Sometimes searching for things in the Software Center does not find something if you enter a specific package name, like *ubuntu-restricted-extras* because it titles it without the hyphens, but it can find it if you just search for *restricted*, whereas, synaptic uses actual package names used by apt-get.

3. Port forwarding is only necessary if you want to access something on a home computer **from the Internet**, and then you would need to know your public IP (which for most people is dynamic and could change). You should make sure that you only open ports to things that are secure (for ssh it is best to disallow passwords and instead use shared keys). Port forwarding is NOT necessary to connect between different computers on your LAN.

---

