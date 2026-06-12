---
title: "Mouse/display problem with KVM switch"
date: 2007-01-03
forum: General Help
---

### Post by dazza1234 on 2007-01-03
I am new to Ubuntu and have configured the system to run on a new PC bought specifically for Ubuntu. I loaded the default setup from the live disk (Kernel 2.6.15-27-386) and it all works OK so far. I only have one monitor and keyboard and want to switch between other computers running other systems using a Belkin Omniview KVM switch.

If I switch from the Ubuntu computer to use the mouse/keyboard/monitor on another PC and then back again to Ubuntu, it goes crazy. The mouse flicks all over the screen, random desktop images duplicate and flicker. In other words it's reboot time and totally useless for me.

Any suggestions on how to fix before I junk the whole thing. I'd be happy to have Ubuntu working in a simple console mode if necessary.

---

### Post by Soarer on 2007-01-03
I've had the same problem and if you do a search you will find a lot of other people have too. I eventually got a Belkin 2 port USB KVM with captive leads which worked fine, including audio. Unfortunately, about 6 months in the unit itself broke so I binned it. PS2 connectors seldom work, I understand.

Now I boot into Ubuntu and use NX ([www.nomachine.com](www.nomachine.com)) and Webmin to control a Ubuntu server and Gnome-RDP to control a Windows XP machine. Both work full screen, but Gnome-RDP was the only thing that allowed me to leave the audio on the XP machine. I'll probably move to NX when version 3 comes, if it can do the same with RDP connections. I use a single keyboard, mouse and screen and have the other systems open on separate desktops. This also means I can run the XP machine, which is a work laptop, but only connecting a network cable, rather than screen, kb & mouse.  Also the noisy server can sit in a cupboard.

Might be worth a try - gets rid of A LOT of cables :)

---

### Post by dazza1234 on 2007-01-03
A nice suggestion Soarer, but a lot of extra work to set up. As you note, searching on KVM and Belkin gets a lot of results. One is to change the mouse protocol to "auto" or "IMPS/2", which didn't work for me. Some people report success changing from PS/2 to USB, and others the from USB to PS/2. Plugging a mouse directly into the Linux box is an obvious solution. See
[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=2124&highlight=belkin+kvm](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=2124&highlight=belkin+kvm)

Someone here has a rather ingenious solution with a script that resets the mouse every 10 seconds:-
[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4273](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4273)
which I'm not brave enough (or knowledgeable about) to try out yet.

Sadly, it seems the problem is in the 2.6 Kernel and it seems to be hit or miss whether any of the above solutions will work on an individual system. See
[http://www.linuxquestions.org/questions/showthread.php?postid=778557#post778557](http://www.linuxquestions.org/questions/showthread.php?postid=778557#post778557)

For me, the simple solution is just to unplug the mouse from the KVM box and then re-plug it. I am fortunate in that my KVM box is within arm's reach of where I work. Even if I have to do that little act 100 times a day for the rest of my life, it will still take me less time overall than time I've spent trying to solve it so far!

---

### Post by Soarer on 2007-01-03
Yes - that works too :)

Gnome-RDP is a snap to set-up, and 'just worked' for me. NX is OK too as long as it works first time - if not I have spent a few days wrestling with it (previous version).

I have an MS Natural Pro k/b, and plug my MS optical mouse into one of it's USB ports for convenience. Very occasionally, this exhibits similar behaviour but a quick unplug-plug fixes that too. 

Nothing is perfect, I guess :)

---

### Post by MJN on 2007-02-20
Sorry for arriving late at the party but I thought you might be interested in my fix for this issue.
 
When switching PCs if the mouse starts going crazy then try the following:
 
```

sudo modprobe -r psmouse
sudo modprobe -a psmouse

```
 
This works for me every time (although my mouse is a PS/2 mouse hence USB mice might be different). Obviously it requires either console window being open or you switching to another tty (e.g. CTRL-ALT-F1), logging in, and enterning the commands.
 
To mitigate the chance of it happening I do find that once the KVM has changed over if I leave it a second or so before moving the mouse then the problem doesn't occur in the first place.
 
Mathew

---

### Post by Unconscious on 2007-03-30
The problem is the KVM switch. 

The Belkin Omniview simply doesn't handle the mouse protocol completely, just enough to do windoze.

For my personal sytems I have a 4 port KVM from Planet Technologies, which works great. 

At work I have a 2 port LinkSys KVM which also works well.

---

### Post by cogadh on 2007-04-01
Check the last post in this thread: [http://www.ubuntuforums.org/showthread.php?t=205640&highlight=mouse+wheel+KVM+module](http://www.ubuntuforums.org/showthread.php?t=205640&highlight=mouse+wheel+KVM+module)
It painlessly fixed all my KVM/mouse problems without having to install more software or get a different KVM (I have a cheap Belkin that works great now)

---

