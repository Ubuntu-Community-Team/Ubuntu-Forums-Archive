---
title: "Black screen, 'loading' cursor, on boot"
date: 2007-04-11
forum: General Help
---

### Post by amosharper on 2007-04-11
Hi,

I've been using the beta of Feisty for two or three days. Today I ran the update, changed one of the logon options - can't remember which, sorry - and now it runs the boot loading bar, then hangs with a black screen. The 'loading' circle replaces the arrow cursor.

I'm dual-booting with WinXP and I can see my Linux partition using Explorer2fs, but can't boot in Recovery mode or otherwise for any of the Linux kernels listed on the GRUB menu.

Also, when I boot from the LiveCD, it repeatedly throws a command-line error (about the hard disk, I think).

Any ideas what's wrong and how to fix it, avoiding a format if I possibly can?

Thanks in advance,

- Amos

---

### Post by amosharper on 2007-04-11
Quick update, hope this helps you help me:

Pressed alt-backspace a few times and got this on a blue screen:

**> The display server has been shut down about six times in the last 90 seconds. Something bad is probably going on. Waiting for 2 minutes before trying again :0. <OK>**

I press OK, then ALT-F4 and get a command prompt with the following line already there:
[B]> 
Ubuntu feisty (development branch) Amos-Ubuntu tty4[/B]

It asks for my login info, which I give it. I get a terminal-like prompt. On typing xkill, thinking to close anything that's causing a problem, I am told:

> **Unable to open display "".**

Any ideas? Please!

Thanks again,

Amos

---

### Post by amosharper on 2007-04-11
Please, I need some help!

I took some pictures, see [http://s136.photobucket.com/pbwidget.swf?pbwurl=http://w136.photobucket.com/albums/q187/amosharper/.my_first_widget.pbw&os=1&t=1176312811](http://s136.photobucket.com/pbwidget.swf?pbwurl=http://w136.photobucket.com/albums/q187/amosharper/.my_first_widget.pbw&os=1&t=1176312811)

Cheers,

Amos

---

### Post by diwas on 2007-12-10
Hey this happens when your screen resolution doesnt matches with the pre-defined resolution of the boot screen. You can do this:
Code:
sudo gedit /etc/usplash.conf Set 1 step down resolution you want, eg, if u use 1024*768 as ur default screen resolution, use 800*600 resolution...you will get it.

It worked for me...hope it does to u too.

---

