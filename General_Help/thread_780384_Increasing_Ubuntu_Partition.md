---
title: "Increasing Ubuntu Partition"
date: 2008-05-03
forum: General Help
---

### Post by blah569 on 2008-05-03
Is it possible to safely increase the amount of gigs that your Ubuntu partition has?  I obviously installed Ubuntu with Wubi, as I am posting this in the Wubi forum.  Thanks.

---

### Post by avtolle on 2008-05-03
> **blah569 said:**
> Is it possible to safely increase the amount of gigs that your Ubuntu partition has?  I obviously installed Ubuntu with Wubi, as I am posting this in the Wubi forum.  Thanks.

Yes; see [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by blah569 on 2008-05-03
> **avtolle said:**
> Yes; see [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

I meant to take more gigs from my Windows partition and add them to my Ubuntu partition.  (I am sorry if that link aids in what I am attempting to do, but I did not find such in the link.)

---

### Post by avtolle on 2008-05-03
> **blah569 said:**
> I meant to take more gigs from my Windows partition and add them to my Ubuntu partition.  (I am sorry if that link aids in what I am attempting to do, but I did not find such in the link.)
That I do not know. Sorry about the confusion concerning your OP.

---

### Post by wilsonq77 on 2008-05-03
Try clicking the install icon on the desktop that Wubi leaves and go on the partitioner (keep hitting forward 'till you get there) and edit the entries.

---

### Post by blah569 on 2008-05-03
> **avtolle said:**
> That I do not know. Sorry about the confusion concerning your OP.

Thank you for the postings,  but does anyone have an ideal solution to my inquiry?

---

### Post by drsox1899 on 2008-05-03
Try using PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It's a clone of Partition Magic (Symantec Windows App) and runs as a live CD. I have found it to be very good.

Defrag your Windows Partition first else you may lose some of your Windows data !!

Luck

---

### Post by ago on 2008-05-03
> **blah569 said:**
> I meant to take more gigs from my Windows partition and add them to my Ubuntu partition.  (I am sorry if that link aids in what I am attempting to do, but I did not find such in the link.)

Wubi does not use a real partition only a file inside windows. Hence it is not possible to "take space off windows and give it to Ubuntu". What you can do is add an extra virtual disk (windows file) and move files over.

---

### Post by blah569 on 2008-05-04
> **ago said:**
> Wubi does not use a real partition only a file inside windows. Hence it is not possible to "take space off windows and give it to Ubuntu". What you can do is add an extra virtual disk (windows file) and move files over.

Thank you, but how do I increase the virtual disk?

---

### Post by zaivala on 2008-05-04
I would think that the writers of WUbI would want to put something in here.

I used WUbI because every other installation of Linux on my system gave my HP-modified Windoze a major illness.  Ubuntu works MUCH better than I ever could have hoped, and I'm migrating more and more of my work over into my Ubuntu folder.  I already gave it the maximum 30 Gb size (there should be a box to enter an "other" size), but I have a 250 Gb hard drive and only about 25 Gb is taken up by my Windoze stuff, much of which is music and picture files which would be a lot easier to access if it were in my Ubuntu user area... but there may not be room for it all there.

So, I will echo the request:  Is there a way to increase the size of my Ubuntu folder (on my Windows NTFS drive)?  If not, can it be added (soon)?

Moss

---

### Post by ago on 2008-05-04
[https://wiki.ubuntu.com/WubiGuide#he...90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#he...90d7ef322de99c)

---

### Post by zaivala on 2008-05-04
All I see there is how to increase the "virtual disk" size... if that is the same thing as increasing the folder size, they should be clear about that...  Also, many of the fixes have not been updated for use in 8.04.

Please explain?

Moss

---

### Post by ago on 2008-05-05
I have uploaded a small script to add extra virtual disks.

Follow the instructions in:

[https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by zaivala on 2008-05-06
OK, noobie here.  I downloaded the script, and it didn't run... the script being "wubi-add-virtual-disk" ... how do I install the script?  Being stoopid, I thought that maybe the line you listed, sudo sh wubi-add-virtual-disk /home 15000, would do it, but it didn't.

Hugs,
Moss

---

### Post by ago on 2008-05-06
Unless you are already in the same folder containing the script, you have to add the path to the folder, so if you saved into your Desktop it will be:

sudo sh ~/Desktop/wubi-add-virtual-disk /home 15000

---

### Post by zaivala on 2008-05-06
Thanks!  You're the best.  I got some weird messages in Terminal during the process...

[23: Illegal number: 38%

and at the end...

cp:  cannot stat 'home.backup/zaivala/.gvfs': Permission denied

Cannot STAT?  Do they mean START?

Moss

---

### Post by zaivala on 2008-05-06
OK.  I'm screwed.

I figured it out... just don't know how to fix it.

You just told me to create a new virtual disk -- called Home.  Since I'm too stoopid to know what I'm doing, I did just that.  I could have named it ANYTHING ELSE... but now, Ubuntu thinks it's looking for its files and programs and everything in the NEW disk called Home, while they are in the original disk's section once called Home.  Guess what? I'm in Windoze again.  Nothing works, can't even GET to Terminal to fix it.

Any ideas?

I went into my Windoze files and changed the filename of the new Home to Home2 (keeping the extension).  Hope that works.

Moss

---

### Post by ago on 2008-05-06
Does it complete successfully anyway?
If not,

Edit the script and add 

set -x

on the 2nd line, so that the file starts as follows:

#!/bin/sh
set -x
usage="\nWrong arguments. The function should be invokes as follow:\n\n\t$0 target_directory size_mb\n\nFor instance, in order to move /home to a dedicated virtual disk of 15000MB use:\n\n\t$0 /home 15000\n"
...

Then post here the terminal output
The cannot "stat" is correct since when copying files over the file might not be accessible
Note that after a successful run you have to undo the changes manually first if you want to run it a second time on the same target partition.

---

### Post by zaivala on 2008-05-06
> **ago said:**
> Does it complete successfully anyway?
If not,

Edit the script and add 

set -x

on the 2nd line, so that the file starts as follows:

#!/bin/sh
set -x
usage="\nWrong arguments. The function should be invokes as follow:\n\n\t$0 target_directory size_mb\n\nFor instance, in order to move /home to a dedicated virtual disk of 15000MB use:\n\n\t$0 /home 15000\n"
...

Then post here the terminal output
The cannot "stat" is correct since when copying files over the file might not be accessible
Note that after a successful run you have to undo the changes manually first if you want to run it a second time on the same target partition.

Oh yeah.  It completed successfully.  But now I can't get into Ubuntu.  Period.  I get to the login and password, and it says it can't use Home, do I want to log into Root?  I say OK, it says some other error message, and I'm back to the login and password game.

I could reinstall...  but would lose a few files. HELP!  Please read my previous post, I was as clear as possible as to what happened.  If I didn't have Windoze, I would be posting this from another machine.

Moss

---

### Post by ago on 2008-05-06
To fix it:

boot in recovery mode

0. sudo -s
1. umount /home
2. run: `nano /etc/fstab` and remove the line that starts with /host/ubuntu/disks/home.disk 
3. rmdir /home
4. mv /home.backup /home
5. check that you have the right files in /home (ls /home) and reboot


It would help if you could find out more about the exact error. In particular is /home mounted at all once you are at the login screen? Press ctrl + alt + f2 and then post the content of `ls /home` and `mount`

---

### Post by zaivala on 2008-05-06
I'm sorry, that was not English.  How do I boot in "recovery mode"?

Please remember, I'm a noob.  I am running Ubuntu under Wubi, because I couldn't find any other way to load Linux on this HP a1020n (see my thread on that issue).

Moss

---

### Post by ago on 2008-05-06
When you boot press esc at the countdown after selecting "Ubuntu" and choose the second option. Again, I would appreciate more details on the actual error message before you try to fix it :)

---

### Post by ago on 2008-05-06
If you provide me more info I can try to give you an easy fix.

Then do this.

Boot normally
Press ctrl+alt+f2 when you have the login screen
Login to the terminal and post the output of the following commands

ls /home
mount
grep home | /var/log/syslog -A2 -B2

---

### Post by ago on 2008-05-06
Or wait tonight so that I can run some more tests on my own :)

---

### Post by zaivala on 2008-05-06
> **ago said:**
> When you boot press esc at the countdown after selecting "Ubuntu" and choose the second option. Again, I would appreciate more details on the actual error message before you try to fix it :)

You are welcome to appreciate all the error messages you like.  However, I got that from/during the installation process of the new virtual disk, and have NO WAY to get back there until I can get back into Ubuntu.  Thank you very much for your instructions on doing that, but I would prefer not to repeat my error just to get you clearer information on the error messages.

I was also surprised to learn that I cannot cut-and-paste text from Terminal to an email; if I could have done that, you would have had the entire process in an earlier post.

Moss

---

### Post by zaivala on 2008-05-06
OK.  I get the bootup.  I get to Login (enter), Password (enter)

"User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users. [<- OK]"

Recovery isn't helping, or I don't know what I'm doing enough for it to help.

I have a meeting to get to, so I'll be away from here for a few hours.

---

### Post by ago on 2008-05-06
Ah maybe I wasn't clear. I would appreciate more info about the errors that you have AT THE MOMENT. The fact that you cannot login and that /home is kaput does not mean that you cannot use Linux... ;) 

In fact if you follow the above instructions it would help. Basically I need to understand why exactly the new /home does not get mounted when you boot.

---

### Post by zaivala on 2008-05-06
I truly wish I knew enough to help you.  The errors happened when my earlier pre-new-disk installation was still running, which it stopped doing immediately afterward.

I DID follow your instructions.  However, after going to Ubuntu Recovery, it gives me a set of options which are not yet English to me... the only one I understand is "Normal Boot".  If it dropped me to a command line, I would be nowhere that I could do anything.

---

### Post by ago on 2008-05-06
I will have a second look myself and let you know then

---

### Post by zaivala on 2008-05-07
Well, I told you I was an idiot when it came to the command line... your statement "login to terminal" did not give me what I needed.  Typing "terminal" on the bash command line just told me there was no such command.

However, I DO have a book on "Learning the bash Shell" (from O'Reilly), and have just retrieved it from my bookcase (in my roommate's room, waking him up).  I'll get there, I promise.

I still am coming to believe it would be easier to reinstall Ubuntu.  I would only lose a few files... and have to reconfigure my browser with my bookmarks and such...

Moss

---

### Post by zaivala on 2008-05-07
> **ago said:**
> Ah maybe I wasn't clear. I would appreciate more info about the errors that you have AT THE MOMENT. The fact that you cannot login and that /home is kaput does not mean that you cannot use Linux... ;) 

In fact if you follow the above instructions it would help. Basically I need to understand why exactly the new /home does not get mounted when you boot.

I thought I was totally clear that I had to leave Ubuntu and boot to Windows in order to post ANYTHING.  Therefore, I do not still have the original error messages, and cannot get back into Ubuntu to find them with my current knowledge level.  So that error message I just gave you WAS the "error I have AT THE MOMENT" and the only one I can find to give you...

...unless my study of my bash book shows me how to get into Terminal from bash shell and then execute the command you have given me to execute.

[Edited to add:} The book does not even mention opening other programs such as Terminal, as far as I can see in a quick scan.

---

### Post by ago on 2008-05-07
terminal is simply a way to say the command line interface as opposed to the graphical interface.

Anyway, I didn't have time to look at it yesterday. Probably tonight. Feel free to reinstall in the meantime.

---

### Post by zaivala on 2008-05-07
OK then, the bash line interface told me I did not have sufficient permissions to execute that line.  Yes, I logged in and gave my password.

Ah well.  Guess I have to reinstall.  Hate it.

Moss

---

### Post by ago on 2008-05-07
You need to prepend "sudo" to your commands in order to gain the rights...

e.g.

sudo cat /var/log/syslog

---

### Post by zaivala on 2008-05-07
LOL Oh. Ok.  You didn't tell me that... what you said was...

ls /home
mount
grep home | /rar/log/syslog -A2 -B2

Since I only understand about half of that...  where do I put "sudo"?

At any rate, I'm reinstalled.  I guess I'll just leave my Windows files on my Windows side until I can get a decent hard drive in my external drive cabinet and back up my pertinent files.:popcorn:

While I'm here... I keep seeing how many "thanks" you've received in your stats here on the forum... but don't see anything to click on to give you that...  is it automatic with responses?

Moss

---

### Post by ago on 2008-05-07
There should be a small star icon on the bottom right of each post

---

### Post by zaivala on 2008-05-07
Nope, don't see it.  Ah well.  Until I'm ready to try another virtual disk, I'll drop this thread.

Moss:KS

---

### Post by ago on 2008-05-07
I tested the script and it works well for me.

---

