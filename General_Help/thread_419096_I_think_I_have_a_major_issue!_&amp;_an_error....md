---
title: "I think I have a major issue! &amp; an error..."
date: 2007-04-22
forum: General Help
---

### Post by bobleny on 2007-04-22
Where to start!? Well, I am using 6.10 Edgy Eft. I've had the system for quite some time now. I think I have a big problem... :'(

Here are some things I noticed before I realized I had a problem.
-= Random files disappearing. They were not deleted, I checked the trash bin.
-= In the trash bin where files I never deleted. No correlation to the files that disappeared.
-= New files I've never herd of in my /home/bob directory.
-= Dolphin file manager not working correctly. E.g. Not moving files, when instructed too.

Odd right!? So I figured I'd restart the thing and hope it would fix the issue. When I turned it off, I received no problems. When I turned it back on and tried to login, I got this error:

&#8220;Xsession: warning: unable to write to /tmp; x session may exit with an error&#8221;

I click &#8220;OK&#8221; and it takes me back to the login screen....

Before I go on, I would like to mention that Truecrypt has been installed on the computer for almost as long as I've had Kubuntu installed. This means that the Truecrypt program hasn't caused the problem. I also need to point out that I have created volumes in the past with out any problems to the computer. As a result, I feel the following is most likely the reason for this problem!

I was attempting to make two 5gig truecrypt volumes in &#8220;/etc/Truecrypt&#8221;. The first on was made just fine, the second one couldn't finish; I ran out of room! I think that was the problem. Maybe some how, when I ran out of room, it pushed files out of the way and maybe deleted some of them...

I removed the volumes before I restarted the computer.

--------------------
df -th
OK: As it turns out, /dev/hdba2 is full...
Size: 9.4 GB
Used: 9.2 GB
Available : 0 GB
Used %: 100%
Mounted on: /
File System: ext3

I don't know what to do. Please help me.

Thanks a lot!

---

### Post by bobleny on 2007-04-23
Sorry, don't mean to be pushy, but I need to get this thing working. I have work to do on that drive....

---

### Post by bobleny on 2007-04-23
Hey!

I still need a lot of help please! I don't know what to do.... :'(

---

### Post by Grey on 2007-04-23
I wasn't going to post this, since I don't have time to give you proper answers right now (sorry, at work).  But I figure bad help is better than no help.  But it sounds like truecrypt corrupted your filesystem to me.  I would boot into single user mode (sudo init 1), and try to recover the drive.

sudo init 1
umount /dev/sda (or whatever your drive is called.)
fsck /dev/sda

Or something like that... that's from memory.  man fsck should help you with the command.

---

### Post by bobleny on 2007-04-23
I would also like to mention, that Truecrypt has been installed on the computer for almost as long as I've had Kubuntu installed. This means that the Truecrypt program hasn't caused the problem. However, the following may be so!

I just added that to the first post. I felt it was important to point that out.

I appreciate the help, but before I go on, I would like you to know the above in case that changes your thought...

Oh, I should also add that I have made volumes in the past in my home folder with out any problems! I think that also changes things. I will add that to the first post too.

---

### Post by bobleny on 2007-04-24
Still here...

---

### Post by bobleny on 2007-04-24
Hey! :confused:  :'(

---

### Post by phidia on 2007-04-24
I don't have an answer to this but when you have an urgent need for some response it's probably better to try irc i.e. open your preferred chat app go to freenode, channel #ubuntu.

---

### Post by bobleny on 2007-04-24
Can no one solve my problem!? I took your advice and asked on the kubuntu irc channel, but no one has been able to help. I keep asking, but no response......

---

### Post by bobleny on 2007-04-25
Well with a bit of help from #kubuntu, I was able to determine that one of the partitions on my linux hard drive is full. I ran this command, "df -th", and only the one was full... Which must be do to the volumes I created and deleted, or perhaps thought I deleted.

OK: As it turns out, /dev/hdba2 is full...
Size: 9.4 GB
Used: 9.2 GB
Available : 0 GB
Used %: 100%
Mounted on: /

Does this help anyone help me?

---

### Post by bobleny on 2007-04-27
Hello!? Any one out there?

Have I confused you?

You know, if your confused about something, ask! I'll try to clear it up for you...

---

### Post by bobleny on 2007-04-28
...

---

### Post by bobleny on 2007-04-28
...

---

### Post by bobleny on 2007-04-29
Dot, Dot, Dot

---

### Post by bobleny on 2007-04-29
I don't mean to be rude but don't you think it's a bit ridiculous that this thread was made 6 days ago?

Please help!

---

### Post by bobleny on 2007-04-30
...

---

### Post by bobleny on 2007-04-30
...

---

### Post by Sef on 2007-04-30
> Well with a bit of help from #kubuntu, I was able to determine that one of the partitions on my linux hard drive is full. I ran this command, "df -th", and only the one was full... Which must be do to the volumes I created and deleted, or perhaps thought I deleted.

OK: As it turns out, /dev/hdba2 is full...
Size: 9.4 GB
Used: 9.2 GB
Available : 0 GB
Used %: 100%
Mounted on: /

Does this help anyone help me?

Are you using ext3 or another file system?

---

### Post by bobleny on 2007-04-30
Ooo, there is some one out there after all!

Yes, it is ext3

---

### Post by bobleny on 2007-05-01
...

---

### Post by Sef on 2007-05-01
I would use a live cd to either delete some of the files, or save them to a flash drive or external hard drive, and then delete them.

---

### Post by bobleny on 2007-05-01
Delete which files from where?

---

### Post by bobleny on 2007-05-02
...

---

### Post by kelvin spratt on 2007-05-02
a little word in your ear if you post as you are doing at the moment you will get no where go back to the begining make a new post explain your problem with as much detail and as accurate as posible then
you might get a better ressponce i'm not having a go but you need to be less hasty as everybody is not hear at the same time as you

---

### Post by bobleny on 2007-05-02
I know that. I'm just bumping the thread up so it isn't on page 50...

---

