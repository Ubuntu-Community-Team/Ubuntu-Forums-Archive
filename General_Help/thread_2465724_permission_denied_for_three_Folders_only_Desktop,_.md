---
title: "permission denied for three Folders only: Desktop, Documents &amp; Downloads"
date: 2021-08-10
forum: General Help
---

### Post by roler2 on 2021-08-10
I cannot save, move or copy any other Files/Folders nor write to File nor create a File/Folder nor extract. . .well. . .I can't do anything. . .with only three Folders: Desktop, Documents and Downloads. Permission denied every time no matter what. With all other Folders there are no issues. Just those three folders. I am able to view my Flash Drive on Desktop, however I am not able to save, move or copy any File/Folder directly from the Flash Drive to Desktop, Documents, Downloads. 

Lubuntu 18.04.

Please advise if possible.

Thank you.

---

### Post by guiverc on 2021-08-10
Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that only days ago reached it's EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

which mentioned the 3 years and support ending April-2021.

A Ubuntu Weekly Newsletter highlighted the EOL of flavors
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582))

Not all flavors gave EOL notices, but if you look they had dates provided already. eg. Xubuntu mentioned on [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) that EOL was 29-April-2021 (more accurately than Lubuntu's April-2021).

*As for your question - "advise if possible".  I can't see why not as I don't recall any issues.  I'd try copying/moving from a CLI or command prompt (so messages appear on your `lxterminal` and you can see why.  I'm on a modern Lubuntu, but have no issues on my old thinkpad t43 for example that still runs Lubuntu 18.04 as it's x86/i386 only).  If the messages aren't clear, I'd likely explore via `stat` etc. looking for reasons etc*

---

### Post by roler2 on 2021-08-10
So you are saying the discontinuance of Lubuntu-specific updates caused only the Desktop, Documents and Downloads Folders to become unusable via permission denied yet all the other Folders are just fine with full permissions? Why would the discontinuance of Lubuntu-specific updates cause that? So everyone that is still utilizing Lubuntu 18.04 cannot access their Documents, Desktop and Downloads Folders, those permissions seemingly ended in April 2021, and so everyone who is still utilizing Lubuntu 18.04 is receiving permission denied on those three Folders only? You stated that you still have Lubuntu 18.04 on your Thinkpad and you apparently do not have permission denied applicable to your Desktop, Documents and Downloads Folders, then why do I? Your response confuses me.

---

### Post by guiverc on 2021-08-10
No, sorry that is not what I said (*or at least not what I meant*)

I said Lubuntu support has ended; it came with 3 years of support which has ended  (*wearing my Lubuntu hat on if you will*)

I used to have a Lubuntu 18.04 LTS system besides me for support questions, but it's now running Lubuntu 20.04 LTS so I can't boot it up and see. When it was still running Lubuntu 18.04 LTS I had no issues with it.

I'm still running old IBM Thinkpads with pentium M processors (ie. x86 or *i386* only) which were only capable of running Lubuntu up to the last *i386* release (18.10 & 19.04 which weren't LTS so they returned to 18.04).  They still run normally and I have no issues, but I won't use them for support (*as Lubuntu support has ende*d).  

My "*[I]advise if possible*[/I]" opinion was based on a machine I use for support that no longer has 18.04, and old boxes  I personally use but  won't use for support anymore; ie. why I said there is no problem that I'm aware of.  I said what I'd do; ie. I'd use commands to try your *copy* or *move* so you can see reasons, or explore using `stat` etc.

The latest release we had go [EOL included this statement]("https://lubuntu.me/lubuntu-20-10-end-of-life-and-current-support-statuses/")

> After July 22nd, the only supported releases of Lubuntu will be 20.04 (until April 2023) and 21.04 (until January 2022). **All  other releases of Lubuntu will be considered unsupported, and will no  longer receive any further updates from the Lubuntu team.**

I'm a Lubuntu team member *(why the Lubuntu hat*) and you're asking for support for a release we no longer support. I provided a few *vague* clues (ie. *I have no issues on my ancient IBM thinkpad thus how I'd explore was offered*) after providing the official Lubuntu support facts (ie. [*bionic* is EOL]("https://lubuntu.me/bionic-eol/"))

---

### Post by roler2 on 2021-08-10
I utilized Lubuntu 16.04 after EOL and never had any problems with permissions on any Folders or Files. I do not quite fully understand chmod or chown. Obviously something is wrong with the Download, Documents and Desktop Folder permissions because all the other Folders are fine. I can move, copy, paste, write to file, etc. to any other Folder, just not to the Download, Documents and Desktop Folders, yet I can still view my Flash Drive on the Desktop and copy/paste, etc. to any other Folder, just not to Download, Documents or Desktop. If I didn't have trouble with 16.04 after EOL, then why am I having difficulty with 18.04?

---

### Post by ajgreeny on 2021-08-10
From a terminal please show us the output of command ```
ls -la Documents
``` and repeat that command for the other problem folders; the output may tell us what is wrong.

---

### Post by GhX6GZMB on 2021-08-10
> **ajgreeny said:**
> From a terminal please show us the output of command ```
ls -la Documents
``` and repeat that command for the other problem folders; the output may tell us what is wrong.

^^^This.

You obviously have a user/group permissions problem. Did you copy those folders from a different PC, perhaps? 

Lubuntu 18.10 is fine, I ran it until recently, the issue has nothing to do with support.

---

### Post by The Cog on 2021-08-10
I would go for this first, to see the access rights that are applied to the folders:
```
ls -ld Desktop  Documents  Downloads
```

---

### Post by Bashing-om on 2021-08-10
roler2; Well !
- A repeat of my 1st response that did not go through -

Looks like permission issues are at play here.

so
who owns the folders, and what are the permissions when terminal command
```

ls -ld Desktop/ Documents/ Downloads/

```
is executed.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and we see here
[INDENT]what story gets told
[/INDENT]

---

### Post by yancek on 2021-08-11
> I cannot save, move or copy any other Files/Folders nor write to  File nor create a File/Folder nor extract. . .well. . .I can't do  anything. 


Have you been able to do this in the past.  If so, what changes were made immediately prior to this happening as this is definitely not expected behavior.

.>  I utilized Lubuntu 16.04 after EOL and never had any problems with  permissions on any Folders or Files. I do not quite fully understand  chmod or chown   

Using an unsupported version should not be  problem as long as the user knows that s/he cannot get standard updsates in the norml way and the user does not use the internet as secuity updates are no longer available which can potentially jeopardize the system and thus other users on the internet.

The chmod command changes permissions and the chown command changes ownership of files and directories.  Start by using man chmod to get information on the chmod command.  If the instructions seem to cryptic, doing an online search should get many sites explaining the use of the command.

Posting the permissions as suggested in posts above and indicating what changes (if any) were made immediately prior to this happening would be a good starting point in resolving the problem.

---

### Post by roler2 on 2021-08-11
Thank you for all of the super awesome advice! The permissions were a mess and I do not know how the permissions got so messed up. I was able to resolve the issue utilizing chown. Now I am able to copy/paste, move, extract, etc. without any issues.  

Utilizing ls-ld and ls-la really helped determine the permission issues. Thank you again!

---

### Post by Bashing-om on 2021-08-11
roler2 - Outstanding :D

Pleased you were able to work through the issue.

[INDENT]ubuntu
[INDENT][INDENT]fixable
[/INDENT][/INDENT][/INDENT]

---

### Post by roler2 on 2021-08-12
Thank you again for all of the super awesome advice. The ownership changes I made to the three Folders also appear to remain in place after reboot. I hope the extremely helpful advice I received will also benefit all those who are experiencing difficulty with Folder/File permission issues.

---

### Post by ajgreeny on 2021-08-12
Should anyone else have this problem it would be very helpful if you could post the actual commands you used for the successful repair of your permissions or ownership.

You say the permissions were a mess but have not told us what you actually did.

---

### Post by roler2 on 2021-08-16
[https://askubuntu.com/questions/628896/chown-difference-between-user-and-useruser](https://askubuntu.com/questions/628896/chown-difference-between-user-and-useruser)


[https://websiteforstudents.com/how-to-use-the-chown-command-on-ubuntu-16-04-18-04-with-examples/](https://websiteforstudents.com/how-to-use-the-chown-command-on-ubuntu-16-04-18-04-with-examples/)

---

### Post by Seadevil on 2021-09-04
in terminal:    sudo thunar....go to destination folder ...view properties....take ownership

---

