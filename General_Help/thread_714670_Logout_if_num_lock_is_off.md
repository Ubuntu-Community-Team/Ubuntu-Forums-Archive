---
title: "Logout if num lock is off"
date: 2008-03-04
forum: General Help
---

### Post by shiznatix on 2008-03-04
I use the num lock always but with my keyboard layout the num lock key is right next to my end key and I will sometimes push num lock at the same time as end thus turning off the num lock.

The problem with this is that if I have num lock turned off and go to use my keypad, I sometimes won't notice that it is not typing anything and there is some silly combo of keys that you can press there that just automatically logs you out. No, prompt, no save, just BAM!

How do I turn off this "feature" so I can be safe if I don't notice that num lock is turned off?

---

### Post by jeffus_il on 2008-03-04
Maybe you are not logging out, because the logout prompts you first. Maybe your are entering the <Ctrl><Alt><Backspace> which restarts the x server? This makes a difference as to the workaround you can implement.

---

### Post by p_quarles on 2008-03-04
Map the numlock key to a dummy command. Kind of a hack, but that will work.

---

### Post by shiznatix on 2008-03-04
I don't hit control alt or backspace when this happens. I don't know exactally what combo I put in that does anything but it seams like it does restart x more than log me out because it just slams everything down and goes to the login screen, no prompting for anything.

There are no control, alt, or backspace on the keypad so I don't see how this would be the case.

How do I bind a key to null? I would like my num lock to always stay on since I have never used it for anything else. Also, would this change if I change the language of my keyboard because I tend to switch it depending on what I am doing.

---

### Post by p_quarles on 2008-03-04
> **shiznatix said:**
> How do I bind a key to null? I would like my num lock to always stay on since I have never used it for anything else. Also, would this change if I change the language of my keyboard because I tend to switch it depending on what I am doing.
Binding the key to a command will depend on the window manager you are using. 

As for the command to use, something like the following should work:
```
ls ~/nothing
```
That won't do anything in your actual interface, but will spit out a "directory not found" error in tty1. If you don't want that:
```
ls ~/nothing > /dev/null
```

---

### Post by jeffus_il on 2008-03-04
There is a discussion about <Ctrl><Alt><Backspace>, It seems to bother others as well.
See these links:
[https://blueprints.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace](https://blueprints.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace)
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

I think you need to find a way to remap it, will keep thinking ...

---

### Post by jeffus_il on 2008-03-04
It seems that this may solve your problem:
```
Section "ServerFlags"       
	Option "DontZap" "true"      
EndSection

```

added to your /etc/X11/xorg.conf

I took it from here:
[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-x-server-configuration.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-x-server-configuration.html)

I hope this won't cause problems if you do need to restart the x server, should be OK.

---

