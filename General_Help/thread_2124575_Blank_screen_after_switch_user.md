---
title: "Blank screen after switch user"
date: 2013-03-11
forum: General Help
---

### Post by ubunet on 2013-03-11
When I switch to guest account and back to my user again, the screen is blank (black, white or colored - striped). I have AMD Catalyst 12 installed. My netbook is an Acer Aspire 722.

I run Xubuntu 12.10 x32.

---

### Post by neu5eeCh on 2013-07-01
I've just noticed the same problem on my own system. Logging into any account other than my own (Xubuntu 12.04) results in a blank screen and even a black screen.

---

### Post by JRV on 2013-07-01
Try <ALT>-<PRINTSCREEN>-K at the black screen.

I have never seen a machine where all the switch user, suspend, hibernate options work correctly.
This includes Windows and Linux.

---

### Post by neu5eeCh on 2013-07-01
Thanks, but it didn't work. What is that key-combo supposed to do anyway?

Also, I don't think Xubuntu is actually switching users. Something weird is going on. When I choose switch user, then choose "guest" (not guest-acount), I get switched to a blank screen. If  I then ctrl-alt-f7, I'm brought back (or switched) to my own account. All the tty's are available, but for some reason I can't successfully switch users (or I get a blank screen)? I don't know *which* is happening.

---

### Post by JRV on 2013-07-02
<ALT><PRINTSCREEN>-K kills all processes and re-initializes the X server.

A switch user fails on rare occasions on my system and typing <ALT><PRINTSCREEN>-K at the black screen will return me to the login screen.
The <PrintScreen> key is labeled <SysRq> on some keyboards.

> 
The SysRq key is a key combination understood by the Linux kernel, which allows the user to perform various low-level commands regardless of the system's state.


Read more here: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by neu5eeCh on 2013-07-03
Well... it seems I've finally found Xubuntu's (or XFCE's) fatal flaw. Somebody was having this problem [way back in 2007]("http://ubuntuforums.org/showthread.php?t=421038"). If this bug wasn't solved in the intervening _6_ years, I doubt it's going to be solved here. But hope springs eternal...

---

### Post by mblahay on 2013-09-03
This is not limited to Xubuntu. I have regular Ubuntu and experience the same problem. For me I run a multi user environment at home and this causes me a particular problem. If one of my family members hasn't logged in before the switch user screen begins to fail, then there is no amount of changing virtual terminals that is going to get them to their desktop.

It looks to me that the issue is with the virtual gui terminals that are number F7 and up. Each user that logs in will receive the next available number. It is my thought that the login screen is granted a virtual terminal as well. But I have no idea how to resolve this issue.

---

### Post by mblahay on 2013-10-22
Seems that I'm not going to get an answer for this one. I will attempt to log it as a bug.

---

