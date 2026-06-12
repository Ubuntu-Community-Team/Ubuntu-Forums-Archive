---
title: "LiveCD Question"
date: 2005-08-16
forum: General Help
---

### Post by kenexcelon on 2005-08-16
I was looking on Ebay and people are offering LiveCD.  In the description they state that the cd will allow you to get documents and such off a destroyed operating system.  I downloaded the ISO and I cannot see files on my harddrive.  Should I be able to?  If so, how?  I like this distro a lot and will be dual booting it on my new computer with XP Pro.  Any tips on how to do this?

Thank you!   :)

---

### Post by numberexhaust on 2005-08-16
First off welcome to Ubuntu.  I'm not the expert, but I can tell you it's a great OS and you'll have a lot of fun.

I never really tried to access my HDD from the live CD, but I know it doesn't show up by default on the desktop.  What you need to do is check to see if you can access it through the terminal window (not totally sure where it would end up).  Don't be surprised if you can't, however.

If you really want a good recovery live CD, I would recommend Knoppix.  Though it's a little annoying, it does have some good tools and is very good with autoconfiguring hardware.  The KNOPPIX cd iso can be found here:

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html) 

Another thing you're gonna want out of that is when you install your dual boot, use KNOPPIX's qtpartd tool to partition your harddrive.  It works and it's free.  I'm suggesting this because I'm not sure how good the Ubuntu installer is with resizing NTFS partitions (I switched over from another distro that did it for me).

Besides for that have a lot of fun with Ubuntu... it's definately my favorite distro and I hope you'll have a lot of fun with it too.  Keep coming back to this community, it's great for support if you ever need it. \\:D/

---

### Post by jobezone on 2005-08-16
[QUOTE=kenexcelon]I was looking on Ebay and people are offering LiveCD.  In the description they state that the cd will allow you to get documents and such off a destroyed operating system.  I downloaded the ISO and I cannot see files on my harddrive.  Should I be able to?  If so, how?  I like this distro a lot and will be dual booting it on my new computer with XP Pro.  Any tips on how to do this?

Thank you!   :)[/QUOTE]
 If I remember correctly, when entering Places->Computer there is a list of your other partitions/disks in the LiveCD.

---

### Post by 5-HT on 2005-08-17
Not too sure which filesystem you've got on that comp, but assuming that it's NTFS...ubuntu did not auto detect my NTFS disk (though from what I've read I believe that should hopefully be implemented in the next release).

You should (?) be able to manually mount the drive (though I haven't tried), but another option would be to download and burn knoppix (as numberexhaust suggested).

It's a little more geared towards recovery, though not really a main function.

Knoppix did auto mount my NTFS drive...But be careful not to write to it or you may/will corrupt filesystem.

As to looking for it on ebay, that's certainly an option, but it is freely available for download.

Hope you manage to recover your files.

---

### Post by kenexcelon on 2005-08-17
I did download it, I was just browsing on Ebay.  My laptop's OS is runninng really slow, somehow it's infected with several viruses that will not go away.  I'm lucky enough that I got off of dial-up!  Thanks for the reply.  Are there any that are built for recovery?

---

### Post by numberexhaust on 2005-08-17
[QUOTE=kenexcelon]I did download it, I was just browsing on Ebay.  My laptop's OS is runninng really slow, somehow it's infected with several viruses that will not go away.  I'm lucky enough that I got off of dial-up!  Thanks for the reply.  Are there any that are built for recovery?[/QUOTE]
 Yes KNOPPIX is generally used for recovery, but if you're willing to switch to linux I would recommend none other than Ubuntu.  If you want to know more about various linux distros and their pros and cons, visit [www.distrowatch.com](www.distrowatch.com) .

---

### Post by kenexcelon on 2005-08-17
Thanks for the link, looks like Ubuntu is #1.  Ubuntu was what I was going to use for my linux partitions.    :smile:

---

### Post by numberexhaust on 2005-08-18
[QUOTE=kenexcelon]Thanks for the link, looks like Ubuntu is #1.  Ubuntu was what I was going to use for my linux partitions.    :smile:[/QUOTE]
 Really quickly, though, before you jump into assumptions.  Distrowatch only marks the distros by the number of hits each one gets per day, not by which they think is the best.  If you ask me, I would still recommend Ubuntu, but don't let that get in the way of you doing some distro hopping if you have the time.

---

### Post by kenexcelon on 2005-08-18
Ah, ok!  I've tried several live cd's and I like Ubuntu the most out of all of them.  Look and feel seems to be better to me.  Thanks!  Have a good day.  \\:D/

---

### Post by notebooktessler on 2005-08-19
[QUOTE=][/QUOTE]
 hi! it should be no problem to access your windows partition using the ubuntu live cd; open the root terminal, type "cd /mnt" and "mount /hda1". 

however, i have not been able to use linux-live cds to repair ntfs-partitions, because linux can't write on them. if you want to repair a windows partition, i recommend bart's pe ([http://www.nu2.nu/pebuilder/)](http://www.nu2.nu/pebuilder/)).

---

### Post by kenexcelon on 2005-08-22
I was wondering, is it possible for a live cd to use a wireless card?

---

### Post by sinch on 2005-11-10
hi! I've tried mounting my ntfs like you wrote but it doesn't work!
it shows me no such file or directory:(

---

