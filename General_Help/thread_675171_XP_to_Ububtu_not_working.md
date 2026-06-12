---
title: "XP to Ububtu not working"
date: 2008-01-22
forum: General Help
---

### Post by hooligan36 on 2008-01-22
I have been trying to get an XP machine to access my gutsy laptop. I can see and access my gutsy server, but when I try to access the laptop fropm XP, I get an error message that says the laptop is not accessable.

---

### Post by hooligan36 on 2008-01-22
I have been trying to get an XP machine to access my gutsy laptop. I can see and access my gutsy server, but when I try to access the laptop fropm XP, I get an error message that says the laptop is not accessible. 

I was able to get a log in box at first, but it would not take any of my log ins. I then added Samba GUI from the add programs and after that is when I don't even get a login window anymore, just an eror box saying that the laptop was not accessible.

I went in to the laptop and removed NFS and Samba and re-installed them, but still no luck.

Any words of wisdom?

---

### Post by djrobthaman on 2008-01-22
I figured this one out a while back.  This is really annoying.

First, I have to say that what I'm assuming you're trying to do is share a folder on your network from the gutsy laptop and then access it from your XP system.

To do this, open the samba gui program.  Go to server settings.  In the "Authentication" drop down box change the option to "share" and save settings.

That should do it.

---

### Post by wolfen69 on 2008-01-22
xp will not natively see a linux partition without help. here's the fix: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bodhi.zazen on 2008-01-22
Threads merged, please try to refrain from multiple posts on the same topic, it makes it much more difficult to try to help you. If needed you can always edit your OP or post additional information.

---

### Post by djrobthaman on 2008-01-22
> **wolfen69 said:**
> xp will not natively see a linux partition without help. here's the fix: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Ahh yes... I always forget about those things.  The drives I have shared are either ntfs or fat32 so it's not an issue.  

The login issue is still gonna have to be fixed with the sambe server edit though.

---

### Post by rosegarden78 on 2008-01-22
I gave up trying to use Samba or access Linux from Windows because I assume if I switch to Linux because of critical design errors in Windows, why would I trust Windows to write data to my EXT3 system?  Among the many issues that come to mind:

1) Non-standard character formatting - Windows will change apostrophes and other characters into gibberish or hex code in your word documents or write files in proprietary file formats that OpenOffice may not be able to decypher.

2) Long file names - these are easy in Windows but cause headaches, so to speak, because you have to delimit them like mkdir /home/Documents\ and\ Settings/anotherDir
when using the terminal.

Since I use WINE I have yet to find a reason to login to XP except if I had to use CS3 software, Maya and industry stuff.  For home and office and even music recording studio I choose Ubuntu.  Be careful with Windows writing to EXT3 but I understand the software *does* function.

---

### Post by jonandrews on 2008-01-22
I have put a step by step guide to networking Windows / Ubuntu on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Hope this is helpful to you.

---

### Post by hooligan36 on 2008-01-22
Thank you all for your quick replies. I'll try the changes when I get home. 

I apologize for the two posts earlier.

---

### Post by DrMega on 2008-01-22
I know you'll have already looked at this, but I'm going to mention it just in case. In XP, since SP2 the default setting for its built in firewall is to make it effectively invisible on the network.

Can you ping it?

---

### Post by rosegarden78 on 2008-01-22
Here's a thread I participated in discussing a similar issue.
[http://ubuntuforums.org/showthread.php?p=4175880#post4175880](http://ubuntuforums.org/showthread.php?p=4175880#post4175880)

---

