---
title: "Unable to change password"
date: 2020-07-08
forum: General Help
---

### Post by amitarama on 2020-07-08
Hi

Im new to Ubuntu , very green, finding my way with the whole linux thing .  I recently iNstalled dual boot on windows desktop PC , 2 days ago latest version of ubuntu.  I was running the desktop from a usb and trying Ubuntu out.  Then i installed Ubuntu as a dual boot .  I set up password as part of installation.  I set to no password required for login.  when i tried to install software i entered password to authenticate and it was not recognised? Many attempts later i tried to reset password.  from root menu i followed guide which suggested  -   mount -n -o remount, rw /           passwd  (name) 

When i installed dual boot the USB with tryout was still in PC has this caused a problem , i see two listings for ubuntu in root menu

when i get to the new password part the keyboard does not type ?   Any links or suggestions much appreciated , there seems to be a variety of ways of fixing this but 

Ubuntu is now requiring a password to login so i basically have a massive partition on my pc that i cannot use ?

Thanks

---

### Post by TheFu on 2020-07-08
Password entries don't show anything. Not the password. Not any ********. Nothing.  This is a security thing.
BTW, I don't know of any single command that will both mount storage AND reset a password.  The command above isn't sufficient.
The easiest way to set a new password is to boot the system into single-user-mode.  that gets us in as root, then run **passwd <userid>**.

How to boot into single user mode is dependent on the exact release being used.  "Latest" from someone new often is incorrect.  And most of the time a really bad idea for someone new to linux to run the true "lastest" release.

There are a number of other methods too - using a chroot from a Try Ubuntu Live Boot. Probably too complex for someone new.

---

### Post by CelticWarrior on 2020-07-08
Welcome.

Automatic login although allowed isn't recommended at all. Just don't and acquire good safety habits instead.
Given the situation I would boot a live session, open Gparted, delete all Ubuntu partitions ans start over.

---

### Post by amitarama on 2020-07-10
Thanks 

[h=2]Thanks 

I downloaded 

Ubuntu 20.04 LTS, then i created USB aS PER INSTRUCTIONS .  I used tryout version and decided to install , i installed following on screen instructions .[/h]
I seem to have two vewrsions of ubuntu on my pc ?  and they seem to conflict , when i open firefox it says it is already open in another application ? 

Not sure 

will prob remove ubuntu partition and forget it

---

### Post by TheFu on 2020-07-10
> **amitarama said:**
> Thanks 

[h=2]Thanks 

I downloaded 

Ubuntu 20.04 LTS, then i created USB aS PER INSTRUCTIONS .  I used tryout version and decided to install , i installed following on screen instructions .[/h]
I seem to have two vewrsions of ubuntu on my pc ?  and they seem to conflict , when i open firefox it says it is already open in another application ? 

Not sure 

will prob remove ubuntu partition and forget it

There are many "new to you" aspects in running Linux if all you know is Windows. It is a completely different OS, with different techniques and methods AND a very different philosophy than OSX or Windows.  It takes time to learn these things and unlearn things that don't apply to Linux systems.

1st, there are many different GUIs on Linux systems.  The GUI is just another program, not the OS. You can try out at least 20 different GUIs, perhaps 50.  About 10 are popular, so almost everything, every program, will work across all of those different choices.

In some GUIs, if we double-click, the first click may have opened a firefox instance, so the 2nd click would see it is already running an is let us know about it.  It is possible to have multiple instances of firefox, if that is needed, but most of the time, we want only 1 and want to have all "open website" interactions from other programs sent to the 1 firefox instance running.  But with Linux, we have the choice to have it work the way we want, not the 1-way that some SVP at a company thinks is correct.

Linux is about choices.  Today, you probably don't know all the choices you'd like. That takes time, experience, and hanging out with other Linux people to see what they'd done, learned, like and dislike.

But if you aren't willing to put in some time, perhaps deleting Ubuntu is best. Completely up to you. There is a learning curve, though it is 1000x less than it was 25 yrs ago.  Nobody masters Linux in a year or even 3 yrs.  People do become very productive with Linux systems after a few weeks, providing they can learn to think the Unix way and aren't stuck thinking the MSFT way.  But many people can "get around" with Linux using the old MSFT method too.  My mother did for years, but that was because I handled all the admin work for her and setup buttons for her to click to do the 10 things she did.

---

