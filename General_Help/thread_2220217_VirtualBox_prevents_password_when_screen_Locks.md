---
title: "VirtualBox prevents password when screen Locks"
date: 2014-04-27
forum: General Help
---

### Post by sadhu44 on 2014-04-27
Hi. I'm a newcomer to Ubuntu, to Unity, and to 14.04 lts 64 bit. So far so good. Very good, in fact.

I set the screen lock blank after 5 minutes of inactivity, and password was required to return from lock.  

But when I'm in a Virtualbox session (full screen or seamless mode), if the system happens to go into screen lock because of timout, then, although the mouse works, nothing I enter in the keyboard ends up in the login screen.  So I can't resume the active session. Ctrl-alt-Delete, Ctrl-alt-Backspace, Ctrl-Alt-F3 ---   all don't have any effect.

So far, the only way out of this situation is to do a hard poweroff, which doesn't seem like a good thing to do. 

I have since disabled automatic lock screen (will lock screen manually from now on), and will make sure the Ubuntu Unity interface is active before I lock the screen.

Still, it seems like this might be a bug.  

Comments, anyone?


Be Well.

---

### Post by ajgreeny on 2014-04-27
I don't expect it to work but if you use Rt-Ctrl+F, which would normally go to a windowed VB and release the mouse and keyboard from VB, you may be lucky, however, don't hold your breath.

I never use screen lock on my system unless I manually lock it with Ctrl+Alt+L, which I set in all DEs.

---

### Post by mailduff on 2014-04-28
I can confirm the behavior.  If a full screen virtualbox machine has the keyboard/mouse when the Ubuntu 14.04 host locks.  The virtual box instance retains control of the keyboard.  I have been able to get it to return to the lock screen by using the Right Ctrl + F and then clicking around on the top bar a few times to get the shutdown menu or the clock/calendar.  Some times it takes a few clicks up there, but once the top menu responds, you may then enter your password.  The bad news is anything you typed passes thru to the virtual machine.  I was running Windows 8 today and once I got it to unlock, there it its search menu was my host password I'd been typing in.

Found the bug report: [https://bugs.launchpad.net/unity/+bug/1305586](https://bugs.launchpad.net/unity/+bug/1305586)

---

### Post by k999 on 2014-05-08
This issue is also reported on launchpad: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1317396](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1317396)

---

### Post by chrisliaw2 on 2014-05-17
If you have Guest account enabled, you can simply login and logout from Guest account. After back to login screen, you should be able to enter the password again to unlock the screen, with the virtual box still in full screen mode.

If you tried to enter password and the virtual machine was running text editor program there, after you've login, you would notice whatever you type in the login screen (which you can't) will be shown up in the editor!

Good luck!

---

