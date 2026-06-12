---
title: "Where'd my network go???"
date: 2008-02-19
forum: General Help
---

### Post by ladder24 on 2008-02-19
Hi-
   New to Linux, Ubuntu (7.1), and this forum! Everything was working great, then all the sudden my internal wireless card became disabled, and when I try to use the KDE terminal all it says is "WinSCP: this is end-of-file:0" I can't even find device manager under System> Admin.
   Tried to see if anyone else had the same problem...haven't found any thus far. Any help would be great!

---

### Post by GuDoN on 2008-02-20
Hey,

Nobody has replied yet, not too clued up with wireless and ubuntu, because i dont have a wireless card myself!

but try, in terminal as root #     ifup --force eth0

**eth0** being the card's ID
this could be double checked in System > Administration > Network

Oh, and that command, could also be achieved in the *Network * Properties described above!
> System > Administration > Network

---

### Post by ladder24 on 2008-02-20
Thanks for getting back to me. 

Ok, so I think the problem may be more than just the wireless card. As I stated in my first post, my terminal is blank every time I open it, no matter what I do. No matter what I type, I always get that "WinSCP: this is end-of-file:0" message. So I couldn't run the line of command you gave me in your reply, but when I went through Networks, the eth0 card isn't there.

Also, I can only use Ubuntu in recovery mode now (new since the last message). Everything starts up alright, but there's like a square of 300 px or so around my mouse cursor that will only allow the cursor to move vertically up and down, and it looks like the desk top is shifted to the user's right a couple hundred pixels as well. Weird, huh?

The only thing I can think is that when I start Ubuntu up, it displays something about "PCI Bios Bug (with a bunch of digits after it) found) or something to that effect. It isn't there long enough for me to write down whats there and I don't know if this is normal or not, but I thought I'd give it a crack! 

Everything was working so perfectly and I loved Ubuntu...but now that I've got a problem I'm lost!

Thanks again.

---

