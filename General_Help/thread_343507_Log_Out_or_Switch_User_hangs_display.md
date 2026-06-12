---
title: "Log Out or Switch User hangs display"
date: 2007-01-21
forum: General Help
---

### Post by pekkal on 2007-01-21
I run Edgy (Gnome, AMD64) with NVIDIA (last drivers updated).

Switch User, Log Out or <ctrl><alt><back space> kills the display: the SyncMaster 244T receives no signal from the computer. In the case of Switch User all programs remain running. 

Shut Down: the screen is blank and the Ubuntu logo is not shown.

Any ideas on how to trace this, what to do?

Thanks,
Pekkal

---

### Post by pekkal on 2007-01-22
Funny ...

I tried changing the driver back to 'nv' - no help.

But I noticed that if  I boot to the recovery mode (same kernel: kernel 2.6.17-10-generic) and then run "telinit 3" everything works:
- I can switch user
- I can shut down X and get to text screen
- I can shut down and see the text screen

PekkaL

---

### Post by rich36 on 2007-01-23
I've been getting the same thing.  However, I've found that if I log out then log in as someone else, it usually works ok.

---

### Post by pekkal on 2007-01-23
Just removing "splash" from the Grub's kernel parameters seems to solve the issue for me.  Even better, I get to see all the entertaining messages booting up and shutting down...

title		Ubuntu 6.10 Edgy Eft AMD64 on hda4
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro
initrd		/boot/initrd.img-2.6.17-10-generic
boot

PekkaL

---

### Post by kauhl on 2007-01-26
Hi. First post here.
I'm a linux newbie and have been using ubuntu for 3 tough weeks now.
I'm not ready to give up on  gnome, but the switch user / lock session bug is really driving me mad. If I switch users and later try to restore the first user's session, I get a black screen, everything freezes and console is the only way out.

I've been doing some intense googling and found out that many people seem to have the same problem. Whether they're nvidia card (Geforce MX-440) users like me or not. The following posts illustrate that:
[http://ubuntuforums.org/showthread.php?t=259960]("http://ubuntuforums.org/showthread.php?t=259960")
[http://ubuntuforums.org/showpost.php?p=1712842&postcount=17]("http://ubuntuforums.org/showpost.php?p=1712842&postcount=17")


Following some advice from users in this forum, I've used at least three approaches including the one suggested by pekkal in this topic:

1- editing grub file /boot/grub/menu.lst -> remove splash -> use some vga parameters (i.e. vga=788 )
This approach doesn't solve the problem for good. if I switch users and restore a previously open session more than one or two times, gnome still hangs.

2- editing gdm.conf file and setting AlwaysRestartServer=true
The same thing happens, but the user changing performance degrades.

3- disabling Sync to Vblank for X in the nvidia settings utility
This doesn't help at all. 

I've tried some other things like disabling screen savers and stuff. But the bug is still there.
Does anyone have any advice on this? The switch user functionality is very important for me, as I have at least three users at home.

Thanks in advance and pardon my rusty skills in english.

---

### Post by Egils on 2007-02-07
I also get the blank screen when I try to switch users - specifically when I have logged in to a second account without logging out of the first one and try to return to the first account afterwards (with or without logging out of the second account). At the moment I'm running Edgy AMD64 with the nvidia drivers as well. I remember that other Ubuntu installations have also been temperamental when switching users and would sometimes go to the black screen but the problem has now become consistent.

One thing I have noticed is that if you move the mouse around the black screen, the cursor changes as if the text box for the password for logging back in to the first active account is still there. I even tried entering my password after clicking on this space (although I'm sure shouldn't have) but nothing happened. Maybe the login box is there but isn't being displayed? 

Kauhl, thanks for the suggestions - I'm going to try option number 2 to at least see if I can begin switching between active accounts again.

---

### Post by panayk on 2007-08-31
I have the same problem in Feisty 7.04. It doesn't seem to be related to the proprietary ATI driver or Desktop Effects.

EDIT: Option number 2  above doesn't seem to help.

---

### Post by mikeize on 2007-09-29
Has anyone figured this out yet?  I'm using Gutsy beta, with nvidia restricted drivers.  And this problem is really annoying.  Logged in as one user, switch to another, and then when trying to switch back to (still logged in) original user, I get hung at a black screen.  Yes there is a cursor visible, and sometimes it will indicate the presence of a text box in the center of the screen, but username and/or password don't do anything.  Ctrl+Alt+Bkspace USUALLY will unfreeze it (ie, restart x), after giving me a BRIEF flash of my desktop.

We have two users here, so this is really a big deal.  I don't think it's a gutsy-specific problem, since it seems like an old bug, but I can't find a real fix for it.  Anyone?

-mike

---

### Post by ca46717 on 2007-11-27
did you ever solve the black screen issue ?

---

### Post by Mike Zimmer on 2007-12-18
I am having the same problem with Gutsy 7.10. I usually need to perform 2 control alt backspace operations to restore the login screen. Is this logged officially as a bug? If so, is there a place to see its status? 

Thanks
Michael Zimmer

---

### Post by arch stanton on 2008-02-24
I'm also having this problem switching form user A to User B ( happens about 1 out of 3 times i switch users). Sometimes i can CTRL-ALT-F7 and  get a password dialog and get back into user A, other times I have to reboot.. .. annoying!!!

---

### Post by louieb on 2008-02-24
> **arch stanton said:**
> ...Sometimes i can CTRL-ALT-F7 and  get a password dialog and get back into user A...



I've been using Ctrl+Alt+F7 to go back to the 1st user then Ctrl+Alt+F8 get me back to the second user and the GUI come up. 

You can use Ctrl+Alt+F1 , log on to a terminal and run **finger**  and see which tty X is running on. Then Ctrl+Alt+F<tty#> and see if the GUI doesn't come up. 

User switching worked in Dapper,  but has had it problems since then. There are several  reports on user switching in [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

---

### Post by arch stanton on 2008-02-25
> **louieb said:**
> I've been using Ctrl+Alt+F7 to go back to the 1st user then Ctrl+Alt+F8 get me back to the second user and the GUI come up. 

You can use Ctrl+Alt+F1 , log on to a terminal and run **finger**  and see which tty X is running on. Then Ctrl+Alt+F<tty#> and see if the GUI doesn't come up. 

User switching worked in Dapper,  but has had it problems since then. There are several  reports on user switching in [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

I'm trying to test this out, but of course it won't mess up now that i want it too .. a watched pot ....

I'll reply when i can confirm ..  thanks Louieb !

---

### Post by arch stanton on 2008-02-25
Nope Louieb   

no luck have tried the ctrl-alt-f9  .. no luck  just switches to black screen with dead cursor .. ctrl-alt-f7 will switch to user A  ..  still stumped

---

