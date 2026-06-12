---
title: "2 differnet problems: Grub and hibernate/suspend"
date: 2008-06-06
forum: General Help
---

### Post by rogo22 on 2008-06-06
they arent related but i didnt want to start 2 threads, so the first problem is with grub. on first install, i had kernel 2.6.24-16-rt, then updated to 17-rt, then 18-rt.. already had grub set up for dual boot and everything was fine, all were listed, but i had custom colors that i wanted back to normal.. so i used startup-manager to 'restore original settings', and all i have left is kernel 16.. so is there a way to add 18 back.. or is there any need for it? since 16 seems to be fine?

the other i think is a hardware problem.. and is hard to explain/confusing, but here it is: when i use either suspend or hibernate, it wont work. i cant remember which is which, but 

with one, the computer led will stay blue, but will be unresponsive, with a blacked out monitor. 

and the other will do what it is supposed to do, based on the fact that the led turns the orange/yellow it should when in a state such as this, but when i hit the power button again, the system seems to be stuck between states, the computer sounds as if its running (fans and such) but the led stays yellow, and the computer must be turned off by holding down untill everything is off.

the reason i say it may be a hardware issue is that the same happens periodicly with xp and hibernate. but this happens without fail with ubuntu suspend/hibernate

thanks for any help

---

### Post by lalilulelo on 2008-06-07
I can't say anything about Grub, but I'm having the exact same problem with hibernate and suspend. I looked all over the place, but I can't seem to find a fix for this. It may be that this is a widespread bug in the latest version of Ubuntu and we just need to wait for it to be fixed with an update. Perhaps someone can clarify this issue?

Also which version of Ubuntu are you using? I'm having the same problem with 8.04 (Hardy) and I've read in a few places that this is a problem that some people have with 8.04 but not with the previous version of Ubuntu. If this is the case, then someone is probably already working on a fix for the problem and we simply need to wait for it to be fixed.

One thing that you can (and probably should) do is report this bug to someone since this will aid them in finding a solution for it.

---

### Post by rogo22 on 2008-06-07
im using 8.04 also, the ubuntu studio version if that makes any difference, and how do i report the bug

---

### Post by rraj.be on 2008-06-07
I dont have any idea about your hardware but i have solution for GRUB.

I think its hidden.

can you just post me the contents of 
```

gedit /boot/grub/menu.lst
```

---

### Post by Nameless Neko on 2008-06-07
Well, not sure about the hibernate/suspend part, but I think to get back to the latest kernel, you'd just need to update menu.lst on the ubuntu line so the kernel is listed as 18-rt instead of 16-rt.  You'd be best off making a backup of the menu file first though, just in case something gets messed up, or just make a new menu entry for it to test it and leave the original in place as a backup.

---

### Post by rogo22 on 2008-06-07
well that was easy enough,thanks, but now how can i set something to start automatically, i want 'compiz fusion icon' to start when ubuntu boots up and cant find the application to do this

---

### Post by rraj.be on 2008-06-07
Its too very simple to make a program work at start up

just you can use 

System --> Preferences -->Session to make this.

you can select the required to start at boot up.

---

### Post by rogo22 on 2008-06-07
thanks, i just registered today and am already getting all these questions answered lol. and nobody knows anything about the other issue? lalilulelo mentioned they have the same problem, so is it a known thing? its the only thing keeping me from using ubuntu as my main os, so thatd be great if i can get it working

---

### Post by rraj.be on 2008-06-07
to thank any one one, if the post really helped you and if you really wan2 thank then you can click the medal symbol near the particular post.
I will try to check for the hardware error.

But i asure that every thing in ubuntu ahs been patched and fixed within two to three days of fist found bug or crash.

So you can use Ubuntu as your main OS without any fear.

Allready there are bug reports regarding that and i hope you will be cleared soon.

```
[Bug report 1]("www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg866749.html")
```

```
[repot 2]("lists.opensuse.org/opensuse-bugs/2007-08/msg02543.html")
```

---

### Post by lalilulelo on 2008-06-07
Yes, I was skeptical when I first installed Ubuntu as well, but I'm amazed by how well programmed it is and how quickly the community responds to problems like these.

---

### Post by rogo22 on 2008-06-07
what are those 2 reports for, rraj.be? and how can i do a hardware check, because im almost positive that that is what it is

---

