---
title: "Best way to transfer and sync data on network?"
date: 2007-12-20
forum: General Help
---

### Post by mikey12345 on 2007-12-20
Hi,
Hope someone can offer some good ideas for this.

I've got a Windows machine (Main one used).
I've got an NSLU2 (Used as storage to access from Windows machine and heavly as FTP server).It has about 250GIG of which 100 is used.
I've got an old box running 7.10 with a 400gig HD in - the box does not do much.

*NSLU2 is just a little NAS storage thing.

My NSLU2 runs fine as web server and FTP server etc so not looking to replace it. However i do want to back it up - the ideal place being my old Linux box with 400 gig HD.


My question is what is the easiest way for me to transfer all the files from my NSLU2 (mainly FTP data) to my 400gig drive on my spare box? I'd also like to ensure it automatically updates and syncs each week rather than me doing it manually each week if possible?

Hope this makes sense. 

Thanks

---

### Post by bill.blankenship on 2007-12-20
There's a couple of different ways you could do this.

[FONT="Courier New"]rsync[/FONT] - [FONT="Courier New"]rsync[/FONT] is a really powerful tool for synchronizing files. With the command line options, you could tailor the sync to operate however you wanted (i.e. only sync the MP3 library...) Since it is a command line tool, it should lend well to scripting in order to automate your synchronization. The only drawback that I found when researching this was that [FONT="Courier New"]rsync[/FONT] only syncs in one direction.

Unison - I found a good article under Hack #86 in "Ubuntu Hacks" (O'Reilly, ISBN 0-596-52720-9) about file synchronization. Unison was recommended because it will do bi-directional file synchronization. Another plus is that there is a version ported for Windows (which you listed as one of your requirements...)  I haven't had a chance to play around yet with the Windows port, but I *have* used Unison to synchronize several folders between by Ubuntu Server and Ubuntu laptop, and the process was amazingly simple. I have run across an article talking about how to automate the process, but haven't had a chance to play around with it yet.

Here are a few links for further reading if you're interested:

[FONT="Courier New"]rsync[/FONT] entry at About.com
[[COLOR="Blue"]http://linux.about.com/library/cmd/blcmdl1_rsync.htm[/COLOR]]("http://linux.about.com/library/cmd/blcmdl1_rsync.htm")

Unison project page
[[COLOR="Blue"]http://www.cis.upenn.edu/~bcpierce/unison/[/COLOR]]("http://www.cis.upenn.edu/~bcpierce/unison/")

Article by Micah Carrick
Synchronizing 2 Ubuntu Systems
[[COLOR="Blue"]http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html[/COLOR]]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html")

Happy Hacking!

---

### Post by mikey12345 on 2007-12-20
Thanks.

I've had a quick look at all that but a little confused.


On my NSLU2 i've got 2 folders (One called FTP and the other called DATA) that i wish to back up on to my ubuntu box HD.

I can't install anything on the NSLU2 - well you can but it's limited. Do these programs need anything installing on that? I just want the programs installed on my ubuntu box to 'point' to the nslu2 folders and copy them to the ubuntu box.

I've got samba access and ssh access to the two folders on the nslu2 only.


Could you explain a little more how i would go about this?
Thanks.

---

### Post by mikey12345 on 2007-12-20
Forgot to add the line...

From what i've read RSync needs to be installed on both my ubuntu system and my nslu2 system.

I can't install things on my nslu2 system.


WELL - Actually you can install Rsync on the NSLU2 apparently but looks overly complicated and talks about a 2gig file limit? [http://www.nslu2-linux.org/wiki/HowTo/BackupYourLinuxBox](http://www.nslu2-linux.org/wiki/HowTo/BackupYourLinuxBox)

All i need to do is backup, maybe once a week, two folders on my NSLU2 to my ubuntu drive.

Thanks.

---

### Post by bill.blankenship on 2007-12-20
Since you already have SSH configured on your NSLU2 box, you should be able to accomplish what you're wanting to do by installing Unison on Ubuntu. 

I'm not sure how Unison on Windows will work, but since you have Samba access to those folders, you could probably script something on the Windows box to automatically do the copy.

Happy Hacking!

---

### Post by mikey12345 on 2007-12-21
Just looking on the Unison site more it says i need Unison installed on both systems for it to work?

---

### Post by bill.blankenship on 2007-12-21
My apologies... I didn't realize that it had to be installed on both.  ](*,)

In that case, I think you should probably try just using [FONT="Courier New"]rsync[/FONT].  Since you're primarily concerned with just a one-way sync, that should work just fine.

Let me know if you're having any issues with [FONT="Courier New"]rsync[/FONT] and I'll try to help you through it.

Happy Hacking!

---

