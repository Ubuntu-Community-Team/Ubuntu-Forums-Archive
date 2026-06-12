---
title: "Wine &amp; Windows"
date: 2007-11-04
forum: General Help
---

### Post by L815 on 2007-11-04
I have a dual boot with windows and ubuntu. I was wondering if it is possible with Wine to open up a program already installed on the windows partition, instead of having to re-install it in ubuntu?

---

### Post by hikaricore on 2007-11-04
If this program uses configuration files that are in it's own directory, usually you can.

OR

If said program doesn't really rely much on configuration files and happily runs without or makes new ones.

AND

If said program does not heavily depend on the registry, and entries that have been placed there during/after its installation.

^_^

It's pretty much just trial and error, to be honest.  But [if the program runs under WINE]("http://appdb.winehq.org") and fits these requirements, then you should be good.

---

### Post by L815 on 2007-11-04
:) thanks for the quick reply.

My main reason for asking right now is about Visual C++ or Dev C++ which i'm assuming is heavily dependent on registry etc.. (at least VC++).

 Are there any guides on doing the linking? (I'll look on the wine site for some)

---

### Post by hikaricore on 2007-11-04
Eh, Microsoft products tend to bury themselves deep in the registry even when they don't need to, and then go berzerk when they can't find some usless registry key...

I would honestly suggest a re-install on the Linux side of things, assuimg the program actually works (didn't check myself).

---

### Post by L815 on 2007-11-04
Yah makes sense. I would assume VC++ would give me tons of errors if I try, simply because of what you mentioned.

If I noticed correctly, wine has it's own imitation of registry. If I copy the values over, would it try and read the registry entries from the windows partition or wines? 

If I can get a successful link, I will post my results whether it works or not.

Thanks again for the help :D

---

### Post by weblordpepe on 2007-11-04
You may be interested in virtualisation. Try running Windows in a virtual machine, but connect to it using remote-desktop. There's a tutorial how to do it on this forum.

This dude has all sorts of super Microsoft programs (VC++ too I think) running in his Ubuntu. It's because technically they are running in a virtual machine, but the program is displaying on the Ubuntu desktop via a remote desktop trick.

Have a look here: 
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)
[IMG]http://www.creditlearningcenter.com/images/seamless_screenshot.png[/IMG]
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

---

### Post by L815 on 2007-11-06
Awesome! I'll definitely take a look at that. Might be what I've been looking to do. 

I tried using virtual machine, but it bogs down my computer & with VC++ running, it would be extremely slow ( I can imagine).

---

### Post by weblordpepe on 2007-11-06
A MS development package being slow? Never :P

---

