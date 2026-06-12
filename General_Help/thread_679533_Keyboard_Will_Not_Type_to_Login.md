---
title: "Keyboard Will Not Type to Login"
date: 2008-01-27
forum: General Help
---

### Post by cxixer on 2008-01-27
OK, got this OS installed finally. I had to take my hard drive to a different computer to get it installed, so I put it back in the original computer and it said the x server was not configured properly. So i ran this code: 

sudo dpkg-reconfigure xserver-xorg


went through the configuration to get it to work... now my monitor works fine. After i got back to a command prompt, I typed:

sudo /etc/init.d/gdm start

Now I'm at the ubuntu logo and it asks for a username, I can't type in it! The mouse works, the keyboard works when I am at a command prompt, but it will not let me type into the username field.

Any help is appreciated!

---

### Post by Herman on 2008-01-27
I guess one thing you could do would be to boot into recovery mode and try running through sudo dpkg-reconfigure xserver-xorg again and see if you can get the right keyboard driver next time. Maybe you were just unlucky that time.

---

### Post by polmir on 2008-01-27
You type your password in terminal.
This is hidden operation. That is ok.

---

### Post by shad0w_walker on 2008-01-27
Did you read his problem? He is at the LOGIN SCREEN. Not in the terminal. The typing is not hidden there.

---

### Post by polmir on 2008-01-27
yes
```
man sudo
```

---

### Post by shad0w_walker on 2008-01-27
Read carefully.  [SIZE="6"]HE IS NOT AT THE TERMINAL.[/SIZE]

He is at the graphical login screen. sudo does not come into this.

Read the ******* posts before you keep posting useless information over and over.

---

### Post by polmir on 2008-01-27
Is hidden password only terminal?

read

```
 man login
```

---

### Post by shad0w_walker on 2008-01-27
For starters, yes the password is only completely hidden when typing at sudo or such. In the graphical environments it is masked with some character such as '*'

Also, he is trying to type his USERNAME so what has been said is completely pointless anyway.

---

### Post by seventhc on 2008-01-27
Mine is hidden at login, but I made it that way,(by unchecking show visual feedback in the password entry...in login preferences. ) perhaps it got changed while you were doing something. I would try typing in your password even if you can't see it and try logging in. If you can log in, we can set it back so it shows you feedback if you want. very easy to do. :)

edit...nm, I didn't see that you also couldnt type in your username. sorry

---

### Post by BuffaloX on 2008-01-27
If you use USB keyboard, you might try to enable legacy USB Keyboard in your CMOS settings.

---

### Post by seventhc on 2008-01-27
> **BuffaloX said:**
> If you use USB keyboard, you might try to enable legacy USB Keyboard in your CMOS settings.
It's working everywhere but the login screen so it shouldn't be a keyboard issue.

---

### Post by BuffaloX on 2008-01-27
I've had a similar problem, and i think the above was the solution.
But I may remember it wrong.

---

### Post by cxixer on 2008-01-27
Yeah, I'm not sure what they keyboard issue would be. But the keyboard doesn't even give a signal, the lights do not blink, I can not even turn on number lock or caps lock. The only setting I think I can choose differently is the pc(whatever) ...

Its set to pc104 which was the default, I could try pc101 or something else, any suggestions? 

I havn't had so many dumb problems with a linux distro ever! I wanted to try ubuntu because the live CD came pre-installed with emc, a linux based cnc controller. I might just install another distro in the meantime and try to get emc loaded on it.

---

### Post by seventhc on 2008-01-27
> **cxixer said:**
> Yeah, I'm not sure what they keyboard issue would be. But the keyboard doesn't even give a signal, the lights do not blink, I can not even turn on number lock or caps lock. The only setting I think I can choose differently is the pc(whatever) ...

Its set to pc104 which was the default, I could try pc101 or something else, any suggestions? 

I havn't had so many dumb problems with a linux distro ever! I wanted to try ubuntu because the live CD came pre-installed with emc, a linux based cnc controller. I might just install another distro in the meantime and try to get emc loaded on it.
You did say you could type at the terminal right? Just want clarification to be certain.
Or did it stop working after you ran this command
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cxixer on 2008-01-27
I could type fine using the live cd, I could type fine at the terminal. It just stopped working when I tried to log in.

---

### Post by matthewcraig on 2008-01-27
I have a similar issue, and maybe this fix will work for you.  Try unplugging your USB keyboard, wait 5 long seconds, then plug it in again.  My keyboard is incorrectly detected at boot, but it is detected correctly on re-connect.  I have a bug open on this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82368](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82368)

---

### Post by cxixer on 2008-01-27
it's not a usb keyboard either.

---

### Post by cxixer on 2008-01-27
OK, so for anyone else unfortunate enough to have that problem, I am no help to you. I just switched computers that I installed this OS on, and everything works fine. Whether it is a hardware issue or that ubuntu just doesn't accept a driver, I don't know. But it works on my server, so the computers are getting switched out. 

Thanks for tryin everyone.

---

