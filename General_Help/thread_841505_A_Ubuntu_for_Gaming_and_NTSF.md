---
title: "A Ubuntu for Gaming? and NTSF?"
date: 2008-06-26
forum: General Help
---

### Post by plexxity on 2008-06-26
Is it possible to run Ubuntu with the NTSF file system and be able to install games for PC? is there any linux operating system that can do this?

---

### Post by suicidejack on 2008-06-26
I actually don't know if there is a way to run Ubuntu or any Linux distro for that matter with a NTSF file system.  I do know that Virtual Box is great for running Windows on a Linux machine though and works fine with all of the games I want to play.  I don't know if you have heard of Virtual Box but is a VM (virtual machine) that basically allows you to run Windows as a program inside of, in this case, Ubuntu.  It is a free program and is really easy to set up - I would say it took me less than hour from installing Virtual Box through installing Windows XP on it to have Windows up and running.  There are several great tutorials out there that describe how to go through installing Virtual Box.  I can probably find you a couple of sites if you are interested.

---

### Post by plexxity on 2008-06-26
Neat, ok but i like the fact that ubuntu is so smooth and seems like things run at better frames that windows.. i was trying to find a way to eliminate Windows XP and just use linux for my gaming.. as it would run smoother and better.

---

### Post by dorkdork777 on 2008-06-26
Well, it is possible to install Ubuntu on an NTFS filesystem - but I've never tried it myself, and ext3 is simply better in most ways (you don't have to defragment it, for example). Using NTFS would not help in the slightest with playing PC games, as the filesystem doesn't really matter; it's the compatibility that's the problem. Some games are available for Linux, but for most games you just have to pray that Wine supports it - check [http://appdb.winehq.org](http://appdb.winehq.org) .

---

### Post by WRDN on 2008-06-26
You can't play [most] 3D games in a virtual machine (such as the mentioned Virtual Box) because it doesn't have hardware acceleration.
You could try configuring WINE to play games, or subscribe to [Cedega]("http://www.cedega.com/start/") service (monthly cost).
An alternative is to dual boot Windows and Ubuntu, as you would then get the best of both worlds.

---

### Post by suicidejack on 2008-06-26
Yeah I'm in the same spot as you.  I think that Ubuntu would get a huge following from gamers if they somehow developed a way to have Windows based games somehow work on Ubuntu... I do know that there are several Linux based apps that allow you run Window's games but I haven't checked them out yet.  Here's some of the sites that I was looking at:

[http://www.linux.com/feature/128773](http://www.linux.com/feature/128773)
[http://www.transgaming.com/products/cedega/6.0/](http://www.transgaming.com/products/cedega/6.0/) <-- I've heard a lot about this and several people have recommended Cedega to me - just too lazy to install it now haha.  Here's there homesite: [http://www.cedega.com/](http://www.cedega.com/) It's something that you have to pay for though but its suppose to be good


So I'm eating my own words now... I guess there is a Linux based gaming OS but you have to pay for it:(  It's called MandrakeSoft's Mandrake Linux Gaming Edition if your interested.

Let me know how it goes.  I'm thinking about going with Cedega.

---

### Post by plexxity on 2008-06-26
Seriously if someone could make a way to install windows games easily and 100% compatibaly on linux.. they could make a gold mine! i would pay $500 for such a thing.

---

### Post by plexxity on 2008-06-26
> **suicidejack said:**
> Yeah I'm in the same spot as you.  I think that Ubuntu would get a huge following from gamers if they somehow developed a way to have Windows based games somehow work on Ubuntu... I do know that there are several Linux based apps that allow you run Window's games but I haven't checked them out yet.  Here's some of the sites that I was looking at:

[http://www.linux.com/feature/128773](http://www.linux.com/feature/128773)
[http://www.transgaming.com/products/cedega/6.0/](http://www.transgaming.com/products/cedega/6.0/) <-- I've heard a lot about this and several people have recommended Cedega to me - just too lazy to install it now haha.  Here's there homesite: [http://www.cedega.com/](http://www.cedega.com/) It's something that you have to pay for though but its suppose to be good


So I'm eating my own words now... I guess there is a Linux based gaming OS but you have to pay for it:(  It's called MandrakeSoft's Mandrake Linux Gaming Edition if your interested.

Let me know how it goes.  I'm thinking about going with Cedega.


Ok, cool, i like what i see so far.  Though these games can only be ran in Windowed mode? =O Fullscreen would be nice.

---

### Post by plexxity on 2008-06-26
I have one more question.. Graphics Drivers! Would the games look the same, and perform well with these tools?

Gfx Shaders?
Anti-Aliasing?
DirectX 10?

---

### Post by WRDN on 2008-06-26
As far as I know, DirectX 10 is not supported by any of the solutions posted, yet.
However, I can confirm that Cedega includes support for Vertex and Pixel Shaders 2.0 and below. It does not support anti-aliasing.

---

