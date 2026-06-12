---
title: "Daylight Savings Time Change"
date: 2007-02-06
forum: General Help
---

### Post by gcvisel on 2007-02-06
Do I need to worry about the changes the US will have next month regarding the dates that daylight savings time starts and ends?  Will that be rolled out automatically or do I need to download/change something on my machine like MSers.

Thanks!
Gerry Visel

---

### Post by Vorian on 2007-02-06
Just sit back and let Ubuntu do the work for you :)

You'll have to do nothing.

---

### Post by Maddman on 2007-02-20
How does this work exactly?  Do I have to do an update, or do I need to be logged into a time server somewhere?

---

### Post by Vorian on 2007-02-20
> **Vorian said:**
> 
You'll have to do nothing.
^^
> **Maddman said:**
> How does this work exactly?  Do I have to do an update, or do I need to be logged into a time server somewhere?

and have some popcorn :popcorn:

---

### Post by punx45 on 2007-02-20
> **Vorian said:**
> Just sit back and let Ubuntu do the work for you :)

You'll have to do nothing.

but it can't hurt to spend a couple days  holed up in a bunker with 6 months worth of food and water..  you know.. just in case.

---

### Post by Maddman on 2007-02-21
> **Vorian said:**
> ^^


and have some popcorn :popcorn:

But how does ubuntu know that the daylight saving time has changed?  I mean I believe you, but my managers are going to want an explanation.  If you have some documentation to point me at to read through even, but I don't know what package or service would be responsible for taking care of this.

---

### Post by MystaMax on 2007-02-28
I have the same concerns as Madman. My managers also want to make sure that the applications that run on my dapper server are not affected.

I'm interested in knowing the exact package name I need to install. I prefer not to let aptitude update automatically and perform these actions manually. Thanks in advance guys.

maddman, if I find out before this thread develops anymore, I'll be sure to let you know.

---

### Post by kspringer on 2007-02-28
Check this link:

[Here.]("http://www.ubuntuforums.org/showthread.php?t=367120&highlight=daylight+grep")

This shows you probably already have the update -- and how to check that you do.

k

---

### Post by aleska on 2007-03-11
I'm sorry, but that last post is just made me laugh.  Not poking fun at the author; the info is great I'm sure and very helpful to people.  But isn't it hilarious that the steps for dealing with this new daylight savings in ubuntu is to sit back and relax, maybe have some popcorn, whereas the Windows version is a umpteen step process requiring complicated actions and complete system reboot?  
It times like this I just have to say, Ubuntu rocks!

---

### Post by vayu on 2007-03-11
My output shows Mar 11 and Nov 4 but my time is not changed?

---

### Post by pistcivet on 2007-03-11
> **vayu said:**
> My output shows Mar 11 and Nov 4 but my time is not changed?

Same here (still using Dapper). Had to update my time from the internet.
So much for automation.
Edit:
Some have had problems with an incorrectly set time zone.
Mine was/is correctly set; still no time change.
Oh well, I guess it worked for most people.

---

### Post by dhallar on 2007-03-12
I have a different problem: My time zone is set to Chicago. It should read 8:09. Instead, it reads 9:09. I know that my computer downloaded the time-change update, but it moved ahead 2 hours instead of 1 [I guess]. :confused: Help?

---

### Post by bollix47 on 2007-03-12
> **dhallar said:**
> I have a different problem: My time zone is set to Chicago. It should read 8:09. Instead, it reads 9:09. I know that my computer downloaded the time-change update, but it moved ahead 2 hours instead of 1 [I guess]. :confused: Help?

Not sure if you're dual booting with windows but in my case both operating systems added an hour when they were started up so yes 2 hours is possible.  Just change the time using System-Administration-Time and Date

---

### Post by dhallar on 2007-03-12
Thanks. You guessed it--I'm a dual boot Win XP. Yesterday I had to boot to Windows to use Turbotax. That's when it happened. I'd never have thought of it.
Now I have a new problem: I moved my time back an hour manually. Now my time is correct. But, when I try to go back to "adjust date and tlme" my root password no longer works. I get a " conversation with sudo failed" message. Help again?:confused:

---

### Post by bollix47 on 2007-03-12
Run the following:

```
cat /etc/default/rcS

```
If UTC=yes use gedit to change it to no.

```
gksudo gedit /etc/default/rcS
```

Re-boot and try it again.

---

### Post by FLPCGuy on 2007-03-14
Having the correct settings in the binary file /etc/localtime will insure Ubuntu applies the DST offset when you obtain an update from a time server.  

There are other reasons not yet identified that have prevented some machines from applying the time change, regardless of the UTC setting in /etc/default/rcS.  I have tried both no and yes but still don't get the DST change.  

This thread should be merged with the ongoing discussion at 
[http://www.ubuntuforums.org/showthread.php?p=2297628#post2297628](http://www.ubuntuforums.org/showthread.php?p=2297628#post2297628)

---

### Post by bollix47 on 2007-03-14
My post about UTC had nothing to do with DST but rather the previous post's error re sudo.

---

### Post by FLPCGuy on 2007-03-14
> **bollix47 said:**
> My post about UTC had nothing to do with DST but rather the previous post's error re sudo.
Sorry.  I was just trying to bring this Daylight Saving Time thread up to date with the other one.

I've noticed the same sudo problem after a time change.  This could really screw up Ubuntu if someone set the date way ahead then made a change to a critical system file.  That's one argument for knowing the real root password.

---

