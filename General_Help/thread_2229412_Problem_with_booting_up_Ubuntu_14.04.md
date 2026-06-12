---
title: "Problem with booting up Ubuntu 14.04"
date: 2014-06-13
forum: General Help
---

### Post by Supersonicx10 on 2014-06-13
I just installed Ubuntu 14.04 and I'm having a little trouble booting it up what you mean by that you ask? Take a look at the picture and you'll see why:
[IMG]http://i59.tinypic.com/120m9ex.jpg[/IMG]
If you can't see what it says it says that there were "some major errors trying to find hard drive /" now I don't know what that means but I know it means something wrong here can anybody help?

---

### Post by rahul4557 on 2014-06-13
While installing Ubuntu did install it in seperate HDD or Partitions..??
ie "/" in one HDD and "/home" in another, or something like that?

Try running Ubuntu live and check for the partition table on your HDD..

---

### Post by kansasnoob on 2014-06-13
Do you really mean 14.10?

I mean it's in very early development ATM. The most recent stable version is 14.04 Trusty.

---

### Post by Supersonicx10 on 2014-06-13
It's a [COLOR=#000000]Partition I made it via Windows Vista. "C[/COLOR][COLOR=#000000]heck for the partition table on your HDD"? What do you mean by that?[/COLOR]

---

### Post by Bucky Ball on 2014-06-13
Are you actually using 14.10 and not 14.04??? Please answer this question. :-k

You can't make a Linux partition with Windows so you appear to be quite lost and perhaps should be using something other than 14.10, if that's what you're using.

---

### Post by Supersonicx10 on 2014-06-13
An[COLOR=#000000] early development ATM? What's that?[/COLOR]

---

### Post by Supersonicx10 on 2014-06-13
it's [COLOR=#000000]14.04 why do you ask?[/COLOR]

---

### Post by Bucky Ball on 2014-06-13
> **Supersonicx10 said:**
> it's [COLOR=#000000]14.04 why do you ask?[/COLOR]

Because you said 14.10 in your first post and your thread title. I've changed both. Now that's settled, back to the issue at hand.

Can't see anything in the picture; too small. In future, attach a larger one using the paperclip icon in 'Adv. Reply' (NOT by inserting into the body of the post) or just tell us what the screen says ... that's probably a lot easier ... as you've done here.

Did you actually do a Wubi install? Ubuntu INSIDE Windows? Or have you put Ubuntu on its own partition as part of a dual-boot with Windows? If the latter, do as rahul4557 suggests; boot from the LiveDVD/USB, 'Try Ubuntu' then open Gparted see what you've got. Post a screenshot of it if you want.

---

### Post by Supersonicx10 on 2014-06-13
[IMG]http://i62.tinypic.com/2zr24d5.jpg[/IMG]
How this one I just took it can you read what it says?

---

### Post by Bucky Ball on 2014-06-13
You must have missed this in my previous post: 

> **Bucky Ball said:**
> In future, attach a larger one using the paperclip icon in 'Adv. Reply' (NOT by inserting into the body of the post) or just tell us what the screen says ... that's probably a lot easier ... as you've done here.

No, can't read it.

---

### Post by Supersonicx10 on 2014-06-13
Ok ok I known I should have want with the other one. 

Ok can you read it now about the [COLOR=#000000]Ubuntu icon the flash was on.[/COLOR]

---

### Post by Bucky Ball on 2014-06-13
That's what I mean. Attach it with the paperclip icon in 'Adv Reply'. ;)

What happens when you press the key to ignore? Do you get any further? Let us know exactly what the error is (just write it in a post if not long).

---

### Post by Supersonicx10 on 2014-06-13
> **Supersonicx10 said:**
> Ok ok I known I should have want with the other one. 

Ok can you read it now about the [COLOR=#000000]Ubuntu icon the flash was on.[/COLOR]

It says "the disk drive for /tmp is not ready or not present"

Continue to wait, or Press P to skip mounting or M for manual recovery

---

### Post by Bucky Ball on 2014-06-13
Press 'P'. What's the error?

---

### Post by hakuna_matata on 2014-06-13
If you start "Ubuntu 14.04" from a menu entry in Windows Boot Manager,  it is a Wubi installation. A solution is here:

[http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

Please note that 
> ```
gedit  /etc/grub.d/10_lupin
```
should be
```
gksudo gedit  /etc/grub.d/10_lupin
```

And if you don't see described menu, press shift key immediately after Windows menu.

edit: My answer relates only to Wubi. If it isn't Wubi, it doesn't work.

---

### Post by Bucky Ball on 2014-06-14
... and further to that, Wubi is no longer supported. There are few who know much about it and it has been discontinued (even though it's still available). I wouldn't go there. If you are fiddling with Wubi, think about a regular dual-boot; Windows on one partition, Ubuntu on another.

---

### Post by hakuna_matata on 2014-06-14
> **Bucky Ball said:**
> ... and further to that, Wubi is no longer supported.
**There are different official statements about support: **[http://askubuntu.com/a/449526](http://askubuntu.com/a/449526)

Nevertheless, I don't recommend Wubi. But IMHO in a lot of cases it is easier to [migrate a working Wubi]("https://help.ubuntu.com/community/MigrateWubi") than other solutions.  
[URL="http://askubuntu.com/a/449526"]
[/URL]      [URL="http://askubuntu.com/a/449526"]


[/URL]

---

### Post by Bucky Ball on 2014-06-14
> **hakuna_matata said:**
> **There are different official statements about support: **[http://askubuntu.com/a/449526](http://askubuntu.com/a/449526)



There are not different official statements regarding Wubi (and your link certainly provides none), there is one, from Canonical, and that is that they no longer support Wubi. The link you provided merely tells you how to get around the fact that you are now prompted to do a dual-boot rather than install Wubi if you attempt to install it. 

Having said that, by all means, tweak around it and install Wubi, but there is no support from Canonical and one would find very little help with it here (which is a known fact from past experience). In fact, whether we should offer support for Wubi on these forums at all is currently being discussed by staff. A bit of a no-brainer as there is scant support available for it here as it is. 

Good luck, but again, Wubi is a bit of a dead-end and you'll be largely flying solo.

---

### Post by hakuna_matata on 2014-06-14
> **Bucky Ball said:**
> There are not different official statements regarding Wubi (and your link certainly provides none) [URL="https://answers.launchpad.net/wubi/+question/237642"]
[/URL]Sorry, wrong link. The statement of an official Ubuntu Core Developer is here:
[URL="https://answers.launchpad.net/wubi/+question/237642"]https://answers.launchpad.net/wubi/+question/237642
[/URL][http://meta.askubuntu.com/a/7596](http://meta.askubuntu.com/a/7596)

The Ubuntu Core Developer said:
> Officially it is still supported.... 
And in fact,  a little bit of official support exists because Wubi is on official CD and official release site.

But as I said: Nevertheless, I don't recommend Wubi because in fact, support is very bad. It doesn't matter whether support is official or unoffical.

---

### Post by kansasnoob on 2014-06-14
> **Supersonicx10 said:**
> An[COLOR=#000000] early development ATM? What's that?[/COLOR]

14.10 is in very early development *at this moment* :)

---

### Post by Andrew F in Australia on 2014-06-14
Hi All,

If the OP has Windows on the machine, does this mean that it's possibly set up under dual boot?

I see a similar "unable to access" error on my machine if I shut down Windows incorrectly (ie: hard reboot - press down power key for 10 seconds, or run out of battery on a laptop.)

The fix is to start up Windows in my case and then shut down correctly.  This clears a lock on the drive that Windows places on it so it can then be accessed by Ubuntu on subsequent start ups.

I may have gotten things wrong here, so please excuse me if I have.

Cheers,

AF

---

