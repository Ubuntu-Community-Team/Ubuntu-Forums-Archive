---
title: "Kubuntu shutdown/restart problem, black screen and solutions"
date: 2007-08-14
forum: General Help
---

### Post by tekkenlord on 2007-08-14
Hello Kubuntu users,

The problem I will describe here is a problem experienced by many users (including myself). It is going on for quite a long time now and all the solutions found so far did not work for me. In this post I gather all the solutions and I propose one of my own which worked for me.

The problem occurs when trying to shutdown/restart from the LogOut menu. The screen then just goes black or shows some small colored squares before the usplash appears and the computer hangs there. It does not respond to anything at all except for pressing the shutdown button for 5-6 seconds (hard reboot).

There are three solutions proposed so far (none of them worked for me):

1. First proposed solution:
edit the /etc/kde3/kdm/kdmrc file and add or uncomment the following line in the [X-:*-Core] section (note the *):

TerminateServer=true

2. Second proposed solution:
Instead of shutting down, first logout and then shutdown/restart from the KDM menu.


3. Third proposed solution:
Remove the usplash by editing the /boot/grub/menu.lst and removing the splash option. Usually the kernel line is something like
... ro quiet splash
Just remove the splash so that it looks like this
....ro quiet


My proposed solution is to get rid of the KDM and use GDM instead. So what I suggest is:

install GDM and themes:
sudo apt-get install gdm gdm-themes

Once it finishes the installation it will ask you to select between KDM and GDM. You must select GDM. This workaround works flawlessly for me, I hope it will for you.

---

### Post by cyneuron on 2007-09-04
Thanks for writting all possible solution at one place...

lotta people have this problem....

but you recommend using gdm instead of other solution. Won't that have imapact on performance as gdm will use gnome libs and thus impact performance negatively ?

this thread should be made sticky...

---

### Post by tekkenlord on 2007-09-09
Sorry for the late reply...holidays.

I had the same question from a fella in kubuntu forums. The gdm package does not install the whole Gnome packages since it is just a display manager, not the Gnome desktop environment. It depends on 32 packages and most of them are already installed. 

The problem is that some people tried using GDM but it did not work for them. Another solution I found in the kubuntu forums (that works for me as well) is to install ubuntu and then install kde-core package so that I can have the KDE desktop.

I really do not know why so many people experience this problem and the most strange is that there is not a common solution for all (yet...). Do you experience the same behaviour?

---

### Post by secretkeeper81 on 2007-09-10
> **tekkenlord said:**
> 
The problem occurs when trying to shutdown/restart from the LogOut menu. The screen then just goes black or shows some small colored squares before the usplash appears and the computer hangs there. It does not respond to anything at all except for pressing the shutdown button for 5-6 seconds (hard reboot).

Same problem here.

I'm using Kubuntu 7.04 on a Toshiba Satellite laptop (I'm also having battery power drain problems as explained in a different thread in here, dunno if the two things are related though).

What I'm doing to shutdown properly is just open the terminal and type:

```
sudo shutdown -P now
```

This successfully shuts down the system (although the battery drain problem remains).

---

### Post by tekkenlord on 2007-09-12
Regarding the sudo shutdown -P now:

I had tried that but still sometimes I was getting that garbaged screen. I had also deactivated the splash option from the kernel and I could see what was going on during the shutdown. Apparently, there was no message of unmounting the local filesystems when using that command. Do not know why though...

---

### Post by secretkeeper81 on 2007-10-03
I deactivated the splash screen too.
When I shutdown or reboot using the shutdown command, everything works fine.
When I try to do so using the KDE menu buttons instead, the screen just goes black and no message is displayed; the system won't shutdown or restart untill I manually press the button on my laptop.

Edit: I just found this: [https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43](https://bugs.launchpad.net/ubuntu/+bug/38915/comments/43) and it seems to be working for me!

---

### Post by tekkenlord on 2007-10-03
The TerminateServer=true method is already described in my first post. Unfortunately, it did not work for me as for many others as well. I am glad it worked for you though.

---

### Post by tekkenlord on 2007-10-12
An update to the problem:

Apparently users who experience this behaviour have an Intel graphics card and use the xserver-xorg-video-intel driver. The problem is more severe than I thought and a bug report has already been filed in Launchpad. For more info and tracking take a look at this:

[https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/127101](https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/127101)

The bug is close to finding its solution. Let's hope it will before the release of Gutsy (next week...).

---

