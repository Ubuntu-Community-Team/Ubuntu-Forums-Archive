---
title: "No desktop"
date: 2013-02-23
forum: General Help
---

### Post by Russ_H on 2013-02-23
My sons unity interface stopped working on 12.04 LTS, he is young and is prone to not shutting it down properly, I tried reinstalling gdm via this advice which described the problem

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

However apart from one boot up correctly which failed after I set it to autologin its got a bit worse. I can see the command line OK, so its not damaged and it boots up ok via a USB Ubuntu stick and to add insult to injury its dual boot and Vista is fine, now when I try and manually start lightdm I get 

(Hardware RNG device  inode not found.


"/etc/rc2.d/S21_rng-tools: Cannot find a hardware RNG device to use")

Any ideas?, I tried re installing the rng generator.

---

### Post by schragge on 2013-02-23
Try to uninstall it?
```

sudo apt-get purge rng-tools

```

---

### Post by grahammechanical on 2013-02-23
I am confused.

The link that you provided gives different suggestions on what to try when the OS loads in low graphics mode. Is that your problem? You do not say so. You say the Unity interface stopped working. That is a different problem from low graphics mode.

Another thing, Ubuntu uses LightDM (Display Manager) as the login screen. But you say that you tried reinstalling GDM (Gnome Display Manager). But Ubuntu does not use GDM. So, why try to reinstall it?

You need to give a better description of "Unity interface stopped working." What are the signs and symptions?

Do you see a Grub boot menu? Try selecting Recovery mode and then selecting Resume. If that gets you to a desktop open Additional Drivers and try using another driver.

How old is your son? Is he old enough to have administrator privileges? If he has administrator privileges then I suspect that he has done more than just hit the power off button. I have found Linux to be very resilient.

Regards.

---

### Post by Russ_H on 2013-02-23
> **grahammechanical said:**
> I am confused.

The link that you provided gives different suggestions on what to try when the OS loads in low graphics mode. Is that your problem? You do not say so. You say the Unity interface stopped working. That is a different problem from low graphics mode.

Another thing, Ubuntu uses LightDM (Display Manager) as the login screen. But you say that you tried reinstalling GDM (Gnome Display Manager). But Ubuntu does not use GDM. So, why try to reinstall it?

You need to give a better description of "Unity interface stopped working." What are the signs and symptions?

Do you see a Grub boot menu? Try selecting Recovery mode and then selecting Resume. If that gets you to a desktop open Additional Drivers and try using another driver.

How old is your son? Is he old enough to have administrator privileges? If he has administrator privileges then I suspect that he has done more than just hit the power off button. I have found Linux to be very resilient.

Regards.

Well the symptoms are instead of the Unity Interface I get the error message as mentioned. The problem initially started as the low graphics problem as mentioned and after trying to deinstall and reinstall everything changed to the one I now have, which is the cryptic, to me, message 

"(Hardware RNG device inode not found.


"/etc/rc2.d/S21_rng-tools: Cannot find a hardware RNG device to use")

My son does not have admin rights and grub does work as I would not have been able to boot Vista or reinstall anything under the command line as mentioned.

---

### Post by Russ_H on 2013-02-23
> **schragge said:**
> Try to uninstall it?
```

sudo apt-get purge rng-tools

```

Will try that tomorrow, thanks.

---

### Post by Russ_H on 2013-02-24
> **Russ_H said:**
> Will try that tomorrow, thanks.

No luck, reinstalled it and when it tries to start I get:

 "Starting Hardware RNG entropy gatherer daemon: (failed).

Attempting to get it to start manually does the same thing,

I tried the advice given in

[https://bugs.launchpad.net/ubuntu/+source/gnupg/+bug/706011](https://bugs.launchpad.net/ubuntu/+source/gnupg/+bug/706011)

But it still fails

---

### Post by Russ_H on 2013-02-24
Reinstalling the xserver had no effect.

---

### Post by Russ_H on 2013-02-24
Tried reinstalling gdm, which will not run and lightdm, which will not run. Is there any way of re-installing the entire graphics system?

---

### Post by Russ_H on 2013-02-24
Hi,

   Desktop on sons machine stopped loading, it came up with a "Low Graphics Mode" but would not enter Low graphics but gave an error

(Hardware RNG device inode not found.


"/etc/rc2.d/S21_rng-tools: Cannot find a hardware RNG device to use")

Ctrl-Alt-F1 drops to the terminal.

This seemed closest to the error

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

I have tried reinstalling lightdm, tried gdm which worked once and then failed when I set it to autologin, tried reininstalling rng-tools.

It runs fine from a USB stick, IBM T500 laptop BTW, Vista works OK so its not hardware, is there any way I can copy the files from the USB stick that work to the PC that doesn't. Or is there anything else I can try to get this running?

---

### Post by steeldriver on 2013-02-24
Why exactly do you need rng-tools? it's not part of the standard desktop installation afaik

Did you try purging and NOT reinstalling it? at least just as a check that it is the real issue

---

### Post by QIII on 2013-02-24
*Threads** merged.***

Please don’t start multiple threads with the same subject.  It dilutes the community’s ability to help provide good support and causes confusion.

Thank you and best wishes!

---

### Post by Russ_H on 2013-02-24
> **steeldriver said:**
> Why exactly do you need rng-tools? it's not part of the standard desktop installation afaik

Did you try purging and NOT reinstalling it? at least just as a check that it is the real issue

Thanks, I did not knowingly install rng-tools, I just used the default installation.

I deinstalled rng-tools and I now get a login in screen, it was set to autologin previously, if I log in as me it does not say the password is incorrect but just throws me back to the login screen again, there is a guest session option that alllows me to see a default set up but none of the apps or folders I have under my username. I can still login to the command line OK and see all the files and folders under my user name. At least we have a screen back, so that is progress!.

---

### Post by Russ_H on 2013-02-25
OK I still have a non working system and a child unable to play minecraft. What do I need to do to get this system up and running properly again?. For some reason it will go into guest login ok, will not go to  user name, just throws me out and failsafe graphics will not run. What logs dumps or whatever is needed to get this working?

---

### Post by steeldriver on 2013-02-25
Sometimes that indicates an ownership / permissions problem in the user's home dir - please login at the command line (in a virtual terminal e.g. Ctrl-Alt-F1) and post the outputs of

```
ls -ld $HOME

ls -l $HOME/.{ICE,X}authority
```

---

### Post by Russ_H on 2013-02-25
I have reinstalled Unity and Desktop and it still has not made any dofference, I can get into guest mode but not user mode, just throws me out. I can see everything from the command line but failsafe graphics mode does not work, lets repeat that again because its a little bit counter intuitive ***failsafe graphics will not work***

---

### Post by Russ_H on 2013-02-25
> **steeldriver said:**
> Sometimes that indicates an ownership / permissions problem in the user's home dir - please login at the command line (in a virtual terminal e.g. Ctrl-Alt-F1) and post the outputs of

```
ls -ld $HOME

ls -l $HOME/.{ICE,X}authority
```

Thanks for the reply!

I can only use the command line from "drop to root shell prompt" so its in root, if thats ok.

drwx------ 24 root root 4096 Feb 22 20:13 /root




and 


drwxr-xr-x 2 root root 4096 Jul 24 Desktop
drwxr-xr-x 2 root root 4096  Feb 22 18:58 Documents
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Downloads
drwxr-xr-x 2 root root 4096 Jun16 2012  GNUstep
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Music
drwxr-xr-x 2 root root 4096 Nov 15 21:49 New Folder
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Pictures
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Public
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Templates
drwxr-xr-x 2 root root 4096 Feb 22 18:58 Videos

---

### Post by steeldriver on 2013-02-25
OK if you're logged in at the root console you will have to specify your username explicitly instead of using $HOME i.e.

```
ls -ld /home/*username*

ls -l /home/*username*/.{ICE,X}authority
```We do need to use *username*'s info - not root's

---

### Post by Russ_H on 2013-02-25
> **steeldriver said:**
> OK if you're logged in at the root console you will have to specify your username explicitly instead of using $HOME i.e.

```
ls -ld /home/*username*

ls -l /home/*username*/.{ICE,X}authority
```We do need to use *username*'s info - not root's

OK, sorry.

Its -drwxr-xr-x 49 russel russel 20480 Feb 25 20:33 /home/russel

and a picture attached for the second output as its too much to type in

---

### Post by steeldriver on 2013-02-25
It looks like you typed a space between the dot and the {ICE,X} in that second command - can you try it again exactly as shown please? you should get only 2 lines back e.g.

```
$ ls -l /home/user/.{ICE,X}authority
ls: cannot access /home/user/.ICEauthority: No such file or directory
-rw------- 1 user user 54 Feb 19 17:44 /home/user/.Xauthority
```

---

### Post by Russ_H on 2013-02-25
> **steeldriver said:**
> It looks like you typed a space between the dot and the {ICE,X} in that second command - can you try it again exactly as shown please? you should get only 2 lines back e.g.

```
$ ls -l /home/user/.{ICE,X}authority
ls: cannot access /home/user/.ICEauthority: No such file or directory
-rw------- 1 user user 54 Feb 19 17:44 /home/user/.Xauthority
```

-rw------- russel russel 74800 Feb 22 18:58 /home/russel/.ICEauthority

-rw------- root root 0 Feb 24 13:31 /home/russel/.Xauthority

Thanks

---

### Post by steeldriver on 2013-02-25
OK so because the .Xauthority is owned by 'root', your normal user 'russel' won't be able to write to it, which will prevent russel's X session from starting - from the recovery console try

```
chown russel:russel /home/russel/.Xauthority
```Then 

```
exit
```and continue to normal boot - see if you can log in to the GUI as russel then

---

### Post by schragge on 2013-02-26
If you're doing it in recovery console then you should first remount your root partition in read-write mode to be able to make any changes to it:
```
mount -o remount,rw /
```
That's if you have all your data in one disk partition. If, however, you have a separate /home partition then the relevant command would be
```
mount -o remount,rw /home
```

Then you'll be able to *chown* as **steeldriver** suggested above.

---

### Post by steeldriver on 2013-02-26
Thanks schragge - totally forgot that

---

### Post by Russ_H on 2013-02-26
> **steeldriver said:**
> Thanks schragge - totally forgot that

Thanks to you both!, it now boots in as normal. Minor point, does not worry me that much but if anyone is interested it still will not run in low graphics mode. Also the problem occurred after I had followed the advice to cure the initial problem that seemed to be related to the rng-tools, it did boot into user OK after that but I had to enter the password, I then set it to autologin and that is when the latest problem occurred. If any one wants me to do any further digging around for a bug report then I am happy to do so.

---

