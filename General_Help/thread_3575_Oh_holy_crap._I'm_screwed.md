---
title: "Oh holy crap. I'm screwed"
date: 2004-11-07
forum: General Help
---

### Post by TravisNewman on 2004-11-07
OK I can't sudo, it says there's no password file for root. I can't run anything in the menu that requires root access, I can't su - and I can't login as root. The freakin root account isn't just disabled now, it's GONE. Is there ANY way I can get that back? I need root access to make an account, but root is the account I want to make. I REALLY don't want to have to reinstall. I've put a lot of work into this one.

---

### Post by flygmaskin on 2004-11-07
try running "sudo passwd root". This will let you set a password for root

---

### Post by luiska on 2004-11-07
sudo and all these things uses the user that you created password, but you knew that! :)

---

### Post by TravisNewman on 2004-11-07
[QUOTE=luiska]sudo and all these things uses the user that you created password, but you knew that! :)[/QUOTE]
 yes, but when I try to sudo anything it says... well here I'll give you the exact output:
travis@ubuntu:~ $ sudo passwd root
sudo: no passwd entry for root!
travis@ubuntu:~ $

It does that for anything. If I say "sudo firefox" or "sudo poopybottom" it says "no passwd entry for root." You still have to have the root account to be root in a sudo environment if I remember correctly, no matter whose password it uses. And I had the root account enabled  so I could use webmin, I'd logged in with root before in text mode. So it's all stemming from root being gone, it would seem.

---

### Post by diebels on 2004-11-07
Maybe your /etc/sudoers is screwed. Boot up in recovery mode. If there is no root, you just hit enter, passwd , type in new root password.

---

### Post by TravisNewman on 2004-11-07
[QUOTE=diebels]Maybe your /etc/sudoers is screwed. Boot up in recovery mode. If there is no root, you just hit enter, passwd , type in new root password.[/QUOTE]
 I'll give that a shot, thanks :)

---

### Post by TravisNewman on 2004-11-07
No that didn't work. It never gave me the option to just hit enter, passwd, etc. It actually seemed to boot up exactly the same as always, but this time it gave some errors about root not existing, which I've never seen before.

---

### Post by TravisNewman on 2004-11-07
OK I just tried it with the 386 kernel (I had installed the k7 kernel) and still, it doens't work. I know what the recovery mode you're talking about is, I've seen it before many times, but it's just not going into it somehow. Is there some way I can fix this over the network? Like, taking control of this pc with another or something? Or maybe booting from a livecd to fix it?

---

### Post by az on 2004-11-07
With sudo, you type in your own password.

You have root priveledges with sudo.  There is only one account on your basic Ubuntu system


If you buggered your own password, try booting with the argument
init=/bin/bash
and then run passwd from the console.


Welcome to Unix.

---

### Post by TravisNewman on 2004-11-07
[QUOTE=azz]With sudo, you type in your own password.

You have root priveledges with sudo.  There is only one account on your basic Ubuntu system


If you buggered your own password, try booting with the argument
init=/bin/bash
and then run passwd from the console.


Welcome to Unix.[/QUOTE]
 No my own password isn't messed up, and yes, the root account DOES exist when you install Ubuntu, it's just disabled. I am POSITIVE of this. Without it, apparently, you can't use sudo. It doesn't even prompt me for a password when I run sudo, it just gives me errors about ROOT not existing. I can log in to everything with my own password, but nothing that I need sudo/root access for.

---

### Post by wallijonn on 2004-11-07
[QUOTE=panickedthumb]I just tried it with the 386 kernel (I had installed the k7 kernel)...[/QUOTE]

? Which motherboard do you have - AMD or Intel? 

Computer -> System Configuration -> Users & Groups

doesn't work for adding another user?

---

### Post by TravisNewman on 2004-11-07
[QUOTE=wallijonn]? Which motherboard do you have - AMD or Intel? 

Computer -> System Configuration -> Users & Groups

doesn't work for adding another user?[/QUOTE]

It's an AMD board. 

But no, I can't even get into Computer -> System Configuration -> Users & Groups because it says I have to be root to run it. Same with synaptic, etc. Doesn't even prompt me for a password.

Is there ANY way to copy over the passwd file from a livecd or something? Or maybe a repair operation on the installation cd?

---

### Post by Wombley on 2004-11-07
Note: I'm new to Ubunta but this is how I'd do it on other Linux distros.

Does the following exist in /etc/passwd (should be the top entry):

root:x:0:0:root:/root:/bin/bash

If not, try adding it (you may have to do this from a livecd or from another distro) and trying sudo again. If it does try /etc/shadow - there should be an entry for root, try changing it to (you probably will need to use a livecd here):

root:*:12725:0:99999:7:::

Which is the default for no password. Now try rebooting and trying to sudo with your user password again.

Hope it works.

--Alasdair

---

### Post by TravisNewman on 2004-11-07
Ah flippers! I just remembered what I did, and I don't remember why I did it at this point, but long story short, I'm pretty sure that I DID accidentaly remove the root account. I see the root entry in the passwd file on my other Ubuntu pc, and it's not there on this one. I've been wanting to try out hoary anyway ;) I'd rather not have to though

---

### Post by TravisNewman on 2004-11-07
[QUOTE=panickedthumb]Ah flippers! I just remembered what I did, and I don't remember why I did it at this point, but long story short, I'm pretty sure that I DID accidentaly remove the root account. I see the root entry in the passwd file on my other Ubuntu pc, and it's not there on this one. I've been wanting to try out hoary anyway ;) I'd rather not have to though[/QUOTE]
 wombley: that initially didn't work, but when playing around with the shadow file, I found that most of the built in accounts were account:*:12718:0:99999:7::: instead of 12725, so I used that and it worked brilliantly. I now have the default system with the root account disabled, but happily residing there, and everything works again. Thanks for saving my butt!

---

### Post by humberto on 2004-11-07
[QUOTE=panickedthumb] Is there some way I can fix this over the network? Like, taking control of this pc with another or something? Or maybe booting from a livecd to fix it?[/QUOTE]

Book from the Ubuntu live cd or any other live cd. Mount your root partition (read write) on /tmp. Edit /tmp/etc/passwd and /tmp/etc/shadow, you need to add (at least) the root entry:

in etc/shadow:

```
root:*:12724:0:99999:7:::
```

in etc/passwd

```
root:x:0:0:root:/root:/bin/bash
```

---

### Post by TravisNewman on 2004-11-07
[QUOTE=humberto]Book from the Ubuntu live cd or any other live cd. Mount your root partition (read write) on /tmp. Edit /tmp/etc/passwd and /tmp/etc/shadow, you need to add (at least) the root entry:

in etc/shadow:

```
root:*:12724:0:99999:7:::
```

in etc/passwd

```
root:x:0:0:root:/root:/bin/bash
```[/QUOTE]
 Thanks, but I already fixed everything, that's basically what wombley said earlier. Just out of curiosity, what is the number (in your example 12724) indicative of? There are only a handful of those used throughout the shadow file.

---

### Post by wallijonn on 2004-11-07
[QUOTE=panickedthumb]Ah flippers! I just remembered what I did, and I don't remember why I did it at this point, but long story short, I'm pretty sure that I DID accidentaly remove the root account. [/QUOTE]


 #-o

---

### Post by Wombley on 2004-11-07
[QUOTE=panickedthumb]Thanks, but I already fixed everything, that's basically what wombley said earlier. Just out of curiosity, what is the number (in your example 12724) indicative of? There are only a handful of those used throughout the shadow file.[/QUOTE]

Glad you got everything working. According to [http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html#ss2.3](http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html#ss2.3) its the "Days since Jan 1, 1970 that password was last changed" - i.e. how many days after Jan 1 1970 you installed the system - 12725/365=34.9 years - I installed Ubunta on this system 7 days after you did.

---

### Post by TravisNewman on 2004-11-07
[QUOTE=Wombley]Glad you got everything working. According to [http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html#ss2.3](http://www.tldp.org/HOWTO/Shadow-Password-HOWTO-2.html#ss2.3) its the "Days since Jan 1, 1970 that password was last changed" - i.e. how many days after Jan 1 1970 you installed the system - 12725/365=34.9 years - I installed Ubunta on this system 7 days after you did.[/QUOTE]
 Jan 1, 1970??? Weird. Very weird.

---

### Post by mark on 2004-11-07
[QUOTE=panickedthumb]Jan 1, 1970??? Weird. Very weird.[/QUOTE]This might have the makings of a *very* valuable HOWTO - if you can/will/have-the-time to write it up...

---

### Post by Wombley on 2004-11-07
[QUOTE=panickedthumb]Jan 1, 1970??? Weird. Very weird.[/QUOTE]

Many things on UNIX come from this date - [http://en.wikipedia.org/wiki/Unix_epoch](http://en.wikipedia.org/wiki/Unix_epoch) has more info on this.

[QUOTE=mark]This might have the makings of a *very* valuable HOWTO - if you can/will/have-the-time to write it up...[/QUOTE]

What exactly on? The /etc/passwd and /etc/shadow files? The Unix Epoch? I got the shadow stuff from the Shadow Password Howto at [http://www.tldp.org/HOWTO/Shadow-Password-HOWTO.html](http://www.tldp.org/HOWTO/Shadow-Password-HOWTO.html)

---

### Post by az on 2004-11-07
This is a basic exam question for Unix.  What do you do if you screwed up the root password?  Boot with the argument init=/bin/bash

That makes you root.

You then fix the password.


Anyone who has physical access to your computer can become root.  This is nothing new.

---

### Post by TravisNewman on 2004-11-07
[QUOTE=azz]This is a basic exam question for Unix.  What do you do if you screwed up the root password?  Boot with the argument init=/bin/bash

That makes you root.

You then fix the password.


Anyone who has physical access to your computer can become root.  This is nothing new.[/QUOTE]
 Yeah, that didn't work though, I did just that, and it just booted up normally. I added it to the end of the kernel line. Who knows.

---

### Post by Jos Walrave on 2004-11-08
Try [FONT=Courier New]$ sudo -s[/FONT] :mrgreen:

---

### Post by TravisNewman on 2004-11-08
Hmm. It's been fixed for a while now. But thanks.

---

