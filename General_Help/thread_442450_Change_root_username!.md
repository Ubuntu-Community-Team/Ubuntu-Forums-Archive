---
title: "Change root username!"
date: 2007-05-13
forum: General Help
---

### Post by tic84 on 2007-05-13
Is it possible to login as root, but not have the username root? I want to be able to login as tic, but have complete control of my system without having to type any passwords ever. I know of the security risks, but I just cant be bothered to have to keep typing sudo and su and my password!

---

### Post by bscbrit on 2007-05-13
I _strongly_ recommend that you do not do what you are suggesting.  But, if you insist, this should help:

[http://ubuntuforums.org/archive/index.php/t-31053.html](http://ubuntuforums.org/archive/index.php/t-31053.html)

I you do not want the security benefits of linux, why don't you stick with XP?

---

### Post by tic84 on 2007-05-13
thank you, but I do not want to login as username root, I want to login as tic, but with **_full_** root privileges. I can already login as root. And I dont use linux solely on the basis of its security of windows. In fact, this had no input on my decision to use linux

---

### Post by CocoAUS on 2007-05-13
How about just not having to type a password for sudo?

Edit your sudoers file (try using EDITOR=gedit sudo visudo) and add NOPASSWORD: ALL to your administrator group, or you can add a line specifically for your user.

---

### Post by bscbrit on 2007-05-14
The easiest way is to create a new user called 'tic' and give him full powers, although he will not have the root ID of '0'.  I'm not sure how you rename root to something else.

---

### Post by DoktorSeven on 2007-05-14
Logging in as a desktop (normal) user with full admin privileges is **not recommended** and is very **dangerous**.  Linux has safeguards in place for normal users where they cannot overwrite critical files for a reason.  It is much safer to use your own limited user and use sudo or gksudo to temporarily escalate privileges for certain applications when needed (and only when needed).  Many people who come to Linux from Windows have the same idea that they need a user that has root powers for day to day use, but this is something that needs to be unlearned from Windows, as you see how bad it can be with Windows and even Microsoft is trying to move away from that in Vista.

If you want to log in as a root user for administrative purposes, you can create another user with those rights, but don't log in and run a desktop, etc.

---

### Post by bscbrit on 2007-05-14
DoktorSeven,
If you read the rest of this thread, you will realise that I and others have already pointed out the stupidity of what he is trying to do.
However, he states that he has a valid reason for wishing to do so (without specifying it in detail) and he has asked for help.  That's what I am trying to do - not judge, just help.
But thanks for reiterating what I and others have already advised!

---

### Post by eentonig on 2007-05-14
Any fool who wants to run as admin all the time (because they are used to do so in Windows) will state that he has a valid reason.

But they will also be the first to scream hell that Linux isn't virus free. Or that it 'just crashes'. Basically because htey made it to.

---

### Post by tic84 on 2007-05-16
mmm i cant seem to find a nice way to change this. my reason that i want to do this is because i work on a lot of projects that involve running many tasks and i like to muck around with operating systems and am currently writing a new bluetooth API for my final year project and a lot of the programs require sudo. there is no chance for me of destroying ubuntu using root as i have my os backed up as a bootable dvd, so can perform a low level format of my main partition and copy all the backed up files back to that partiton in less than 10 minutes, so viruses are very low risk for me as my IP is continually changing and I "format" my os once a week.

I could just use the name root to log in, but I really dont like having to be called root :-| and want separate user names with full root power! thanks for any continued assistance and i honestly understand the "dangers" of root lol

---

### Post by eentonig on 2007-05-16
And what's wrong with login in as standard users and then opening a permanent 'root' shel with the command

> sudo bash
In that case, as long as that shell is open, you wont have to type your password for entering commands. But still, I advice against it.

---

### Post by tic84 on 2007-05-16
>  And what's wrong with login in as standard users and then opening a permanent 'root' shel with the command

theres lots of things that i want to run at startup and then continue being able to do as root once i log in. im constantly making programs that i want to run at startup and testing that they run correctly by loggin out/ restarting and logging back in, and i dont want to go through the hassle of adding commands to my rc.local as root, then copying files as root, restarting, then logging in and then typing extra things just because im not root. i simply dont want to type the same things over and over again every few minutes when i restart.

everything works perfectly as root, but i find it hard to believe that its impossible to log in with root privileges with another username

---

### Post by bscbrit on 2007-05-16
For once, you have given a perfectly valid reason for wanting to run your system as root, at least to my way of thinking.  You are aware of the dangers, you have taken reasonable precautions to protect your data and system, and you have a thought of the consequences.

I would rarely recommend running a system the way that you propose, but at least you have convinced me that it is what you want to do.  As I said in an earlier post, I don't judge, I just try to help

Good Luck.

---

