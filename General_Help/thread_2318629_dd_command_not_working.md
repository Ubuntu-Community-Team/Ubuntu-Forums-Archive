---
title: "dd command not working"
date: 2016-03-27
forum: General Help
---

### Post by gilly2 on 2016-03-27
Hi everyone! I'm trying to use the dd command to mount an iso to a usb drive to make a live usb for a different distro of linux. I'm following a tutorial online. When I use the command, it tells me that 0 bytes were copied at 0 kb per second. Why is that happening? Thanks.

---

### Post by yetimon_64 on 2016-03-27
> **gilly2 said:**
> Hi everyone! I'm trying to use the dd command to mount an iso to a usb drive to make a live usb for a different distro of linux. I'm following a tutorial online. When I use the command, it tells me that 0 bytes were copied at 0 kb per second. Why is that happening? Thanks.

It will make it much easier to help you if you copy and paste terminal output of such commands and the results from the terminal to the editor box here in code tags. 

If we can see the actual command and the actual output we don't have to guess so much as to what is actually happening. Also a link to the tutorial you are using will also often be of help to those who can help you, to check the accuracy of what you are following.

[[COLOR=#0000ff]--This post--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") can help you in using code tags if needed. Regards, yeti.

---

### Post by montag dp on 2016-03-28
Let's see, you give almost zero information about what you did and expect us to help.  We're not mind readers.  We don't know what tutorial you were reading online, what command you pasted, or hardly anything about the output you got.  The more information you provide, the more likely someone will be able to help you.

---

### Post by HermanAB on 2016-03-28
Well, you are very fortunate that it didn't work.  If you don't know what you are doing, then dd can overwrite your system disk.

---

### Post by yetimon_64 on 2016-03-28
> **HermanAB said:**
> Well, you are very fortunate that it didn't work.  If you don't know what you are doing, then dd can overwrite your system disk.

A big +1 to what HermanAB has written. Ol' "data destroyer" as it is often nicknamed can be one nasty piece of work.

 @ OP we really need to see the commands/terminal output and tutorial if you want answers. 

As HermanAB notes dd can be a very dangerous tool to use. As a moderately experienced user I have made a simple typing error in a dd command and lost a 75 GB data drive overwritten. Not a nice feeling, I was very lucky to find a relatively recent backup and recovered all but a handful of files. If the mistake affects your root partition then you will be doing a full reinstall, nasty stuff. 

Take care with that command especially if preceded by the sudo command as is likely to be the case when trying to write to a dvd device file for writing an iso image to a dvd/cd.

---

### Post by Bucky Ball on 2016-03-28
> **HermanAB said:**
> Well, you are very fortunate that it didn't work.  If you don't know what you are doing, then dd can overwrite your system disk.

++++1. Takes no prisoners and other ways of mounting an ISO that are safer.

> **yetimon_64 said:**
> A big +1 to what HermanAB has written. Ol' "data destroyer" as it is often nicknamed can be one nasty piece of work.

 @ OP we really need to see the commands/terminal output and tutorial if you want answers. 

+1. Link to the tutorial and post the commands you're using, please (use code tags, see my signature). Unfortunately, we are not psychic. :D

Help us help you. See the pink link in my signature at the bottom of this post.

---

### Post by vasa1 on 2016-03-28
And that's why there's [mkusb]("https://help.ubuntu.com/community/mkusb").

---

