---
title: "Offsite Storage... options and suggestions"
date: 2007-02-24
forum: General Help
---

### Post by HeavyEddie on 2007-02-24
After a recent HD crash on my wifes computer.  Don't worry, it was XP :)  We lost a ton of family photos and other data that simply can't be replaced.

So, I want to create an offsite storage model.  The idea is that she (now Vista), myself and the kids (Ubuntu) can simply save the critical items out to an Ubuntu system on our network.  I was thinking of creating a cron job to FTP the critical files to a server each evening.

So, I guess I'm fishing for better ideas and suggestions.  
[LIST]
[*]SSH?  Haven't used it... is it a good idea?
[*]I would imagine I will need Samba for the vista system
[*]Hosting services?  I use these storage sites, but a regular web host looks like it would be cheaper.
[/LIST]

---

### Post by Skidpad on 2007-02-24
I can't provide much X info (newb user here) unfortunately, but I am interested to see the responses in this thread.

What I can offer, however, your crashed hd - are you sure it's totally dead?  I ask because I've resurrected two hd's recently that wouldn't boot, and could not be fixed (safe mode, fix mbr, etc).  I installed a new hd in each case, reinstalled XP, and then connected the "dead" drive via IDE/USB adapter to retrieve the lost files.  Worked like a champ.  Once I retrieved the files, I then reformatted the drive to use for data backups.  

Just my $.02 if you hadn't considered this option.

---

### Post by outofnicks on 2007-02-25
Not sure how much storage space you need, but gmail gives over 2 1/2 gb of space per account, and I don't know of any limits to the amount of accounts you can have. Just email your files to the gmail accounts from your regular email address. 'Course if you are on dialup this wouldn't be too practical.

---

### Post by Mets on 2007-02-25
Well, I guess the easiest way to do this is to simply buy an external hard drive.  It's a lot cheaper than buying an extra computer to do this.  Plus, even if you do have an extra PC laying around, I doubt it has 300 gigs of storage space.  I got my Western Digital 250 gig external for about $150 and I've never been happier.  It's fast and I have all the data from my PC's backed up on it.  It's also portable and I take it with me when I travel, just to be safe of course :)

Anyway, what are you trying to get out of ssh?  If you are just transferring the files over you don't really need it, any generic ftp server should be secure enough, along with an ftp client of some sort.  If you plan on only storing critical files on that machine and then want to access them on your various PCs, ssh would work.  Just do a ssh -X user@address into the box and type nautilus or konqueror or whatever you use, and you get a file browser.  The network that I am on houses all programs and critical data files on two server banks.  If you want to use, say, MATLAB, you would ssh -X and type matlab and be up and running.

EDIT
Just to mention, if you are going with the latter option I mentioned, you will need XWin (proprietary) or Xming (open source) on the Vista PC to do X-forwarding.

---

### Post by HeavyEddie on 2007-02-25
> **Skidpad said:**
>  I ask because I've resurrected two hd's recently that wouldn't boot, and could not be fixed (safe mode, fix mbr, etc).  

It's a gonner.  I sent it to a company that has successfully recovered many drives for my employer.  Nadda.  In this case the crash was physical.

I'm afraid folks are misunderstanding my question.  Sorry I didn't communicate it very well.  It is important for me to have these files offsite.  This way, short of the entire country blowing up, I will have a backup of what we consider critical files. 

So far, in playing around this is what I have done....
[LIST]
[*]I've created a Samba drive that the XP system can successfully save files to.
[*]*ix systems have this same location mounted without issue.
[/LIST]

So, I guess the big question is... how can I sync this common drive location to an Internet resource?

---

### Post by talz13 on 2007-03-16
I have a dreamhost account, and they offer ~200gb of storage space.  I just set up a nightly cron job that rsyncs my school folder from my server to a directory on my dreamhost account:

```
#!/bin/sh
rsync -e 'ssh -p 22' -avzp /home/shares/school xxxxxx@xxxxxx.com:/home/xxxxxx/ho
meBackups/
```

---

