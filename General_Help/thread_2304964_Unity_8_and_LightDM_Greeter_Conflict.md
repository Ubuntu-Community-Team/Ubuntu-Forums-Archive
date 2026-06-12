---
title: "Unity 8 and LightDM Greeter Conflict"
date: 2015-12-01
forum: General Help
---

### Post by Matthew_Smith on 2015-12-01
Hi,

I recently installed the unity8-desktop-session-mir package and then installed the LightDM Greeter (or a skin for it, rather, from the MacBuntu Transformation Pack), whick worked, but now my system goes straight into Unity 8. I tried installing the Ext2FSD on Windows (I'm dual-booting) and deleting the Unity 8 session package and then rebooting into Ubuntu, but it didn't help. I think I'm gonna go even further and uninstall all the folders and files which contain "Unity 8", but I'm scared that it will make it worse. What do I do? Do I need to delete something else? Please help, as I don't mind getting rid of Unity 8 completely (it's rubbish anyway - only 2 apps and a crazy touchpad...), but I want to have Unity 7 and the Ubuntu I had before, as I had my things on there which are quite important to me. Im sure it's just a matter of deleting some package and rebooting, but which one? Help. And once again, don't tell me to "just reinstall Ubuntu"- as that "just" is a really extreme measure in my case. 

Thanks,
Matt

---

### Post by Matthew_Smith on 2015-12-01
Ok, I deleted all the unity8-desktop-session-mir leftovers (a pre, post, and something else -install file and a .deb file in archives). Will reboot and update. Feel free to post responses in the meantime, as this probably won't help.

---

### Post by QDR06VV9 on 2015-12-01
You should be able to uninstall it by this
```
sudo apt-get uninstall unity8-lxc
```
Reboot all should normal now.

---

### Post by Matthew_Smith on 2015-12-01
Well:
1. I can't boot into Ubuntu AT ALL now, because I deleted those leftover files, so it wants to boot into Unity 8, but can't.
2. I'm not on lxc
and
3.I didn't install Unity 8, i installed unity8-desktop-session-mir.

Oh boy, I feel like I'm in more trouble than I first though...

---

### Post by Matthew_Smith on 2015-12-01
Will now uninstall the LightDM Greeter theme that I installed, and update.

---

### Post by QDR06VV9 on 2015-12-01
Define Delete, Did you manually delete packages or did you use a package manager to remove those.
You can try to reinstall Unity via
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall ubuntu-desktop[/FONT][/COLOR]
```
If that don't work I'm afraid I won't have any more suggestions.
Regards

---

### Post by Matthew_Smith on 2015-12-01
Well, I used windows explorer and Ext2FSD to remove those, and I can't use bash as I cant boot into Ubuntu. Anyway, we're kinda getting close, because it says it can't find the theme folder, but I'm out of ideas. It's up to you guys now.

---

### Post by Matthew_Smith on 2015-12-01
couldn't find a screenshot, but it says that it can't find some html file, page not found is the title, and there's a try again button below.

---

### Post by deadflowr on 2015-12-01
Which version of Ubuntu?
and what lightdm greeter did you install?

unity-greeter works fine with unity8 (for Ubuntu 14.04 and newer) and was already installed.

I refer to the unity8-desktop-session-mir as unity8, which it is.
(the unity8-lxc is a method to run it within an isolated container; but that's a different story)

Also a clarification of whether you where removing packages or deleting files related to those packages.

A possible thing to try:
You might possibly try booting into recovery mode >> enable networking >> run an apt-get update >> reinstall ubuntu-desktop >> reboot.
(Cross fingers)

---

### Post by Matthew_Smith on 2015-12-01
I had Ubuntu 15.10, I installed a theme from the MacBuntu transformation pack, here: [http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html](http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html) . I was removing files related to the packages, you can see which in previous posts. I want to try booting ubuntu in recovery mode, but I don't know how, if you mea the GRUB command line the that's kinda useless.

---

### Post by QDR06VV9 on 2015-12-01
Can you at least get to a tty session?
Meaning can you at a failed login by Key Combo "Ctrl+ Alt +F1
And there you can use the login name and password you normally use to login.
It should show only a blinking cursor
Then try the above command
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall ubuntu-desktop[/FONT][/COLOR]
```

---

### Post by deadflowr on 2015-12-01
> **Matthew_Smith said:**
> . I want to try booting ubuntu in recovery mode, but I don't know how, if you mea the GRUB command line the that's kinda useless.
You can boot into recovery by selecting Advanced Options >> some-kernel-or-generic-something (recovery mode) in the Grub Boot menu.
Will have zero/ziltch to do with anything grub command line.
Trying to switch to a tty(1-6) console session works too.

---

### Post by Matthew_Smith on 2015-12-01
Please look at my last post,explaining that I can;t even boot now, as lightdm says that it cannot find the macbuntu theme that was causing the problem (i deleted it from within Windows). And could you expand a bit more on the recovery mode. what do you mean advanced options? i can only edit the startup code thing or go to a command line.

---

### Post by QDR06VV9 on 2015-12-01
On his site where you installed this theme did you also read this
> Warning: Use this feature on your own risk, last time we received a lot feedback that it is making our system unusable. Please don't report any blank screen (If happens) issue after installing it. BTW it works just fine for me, I can't guarantee you that it will work for you. You have been warned.
And when you say you can only edit the startup code Explain in detail how you can edit that?

Just one more piece of advice never use the delete method when uninstalling things, just don't do this!
When installing packages outside the Ubuntu Stock Repository's make sure you are clear on how to remove that said package.
PPAs can be removed Via the PPA Purge tool
```
sudo apt-get install ppa-purge
sudo add-apt-repository --remove <Your ppa here>
```

Then update and upgrade and autoremove then apt can sort out most of a bad package that was installed.
Don't mean to sound harsh here just the facts.
So for you to remove what you installed off his site you would do this.
```
sudo apt-get install ppa-purge
sudo add-apt-repository --remove ppa:noobslab/themes
sudo apt-get update 
sudo apt-get dist-upgrade
sudo apt-get autoremove
```
Regards

---

### Post by grahammechanical on 2015-12-01
When we install an alternative desktop session and that is what unity8-desktop-session-mir is, we select which session at the LightDM login screen and it becomes the default session until we  select one of the other alternatives sessions that we have installed.

As regards recovery mode we get that by selecting Advance options for Ubuntu at the Grub menu. Installing that lightdm skin most probably overwrote the Unity greeter configuration file and its replacement was not set up to offer login session options.

My advice would be to re-install. I learnt my lesson a few years ago. I do not keep my data on the same partition as Ubuntu and I have another install of Ubuntu to experiment with which I can then easily wipe out with a reinstall.

Regards.

---

### Post by deadflowr on 2015-12-02
Me thinks we are all crossing too many wires here.

It's hard to understand if the OP can access the grub menu or not.
The greeter session for lightdm seems to be a bust,
but that has nothing to do with grub, or the grub menu.

So that would be another thing entirely.
If grub is indeed a problem, then you can fix it with boot-repair.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But if the problem is simply accessing the grub menu, you need to tap the shift key (or esc key if the system is running in uefi mode) right after the initial screen shows; the initial screen that usually says the computer name or such.

Once you get into recovery mode you'll want to enable networking.
This helps for two reasons,
One: having a functional networking will aloow you to connect to the Ubuntu package repository, so you can install packages if need be.
Two:this automatically resets the recovery mode to read/write. Meaning any edits or installed packages will stay installed, otherwise they would be lost on reboot/shutdown.

First thing I might try would be the recommended reinstall of the ubuntu-desktop package.

And the second thing might be to try to set unity-greeter as the greeter session.
To do this you might run
```
nano /etc/lightdm/lightdm.conf
```
if it comes back empty, then perfect. (we'll tackle that in a moment, but:

If it comes back with output, then look to see if there are any lines that say
```
greeter-session=<something-here>
```
in this case change the something-here, or whatever it says, to unity-greeter.

Now back to if it is empty then simply add this
```
[SeatDefaults]
greeter-session=unity-greeter
```
that is it.

to save press ctrl + X then Y then enter.
if you want to see if it works type reboot and find out.

Lightdm reference here:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by Matthew_Smith on 2015-12-02
Nope, recovery mode and terminal fixed it. All it took was deleting the unity8 and macbuntu packages. I knew this, but I just didn't know how to get to recovery - tut, so obvious! Oh well, thanks to everyone for their help...

---

