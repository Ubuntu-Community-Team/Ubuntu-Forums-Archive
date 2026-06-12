---
title: "Removing Ubuntu"
date: 2007-06-29
forum: General Help
---

### Post by Syroco on 2007-06-29
Hey guys, I am going to be removing Ubuntu.  (If you're curious to know, I'm too used to .exe files)

Anyway, I put in my WinXP disc, went into recovery console and typed 'fixmbr'.


Windows XP now loads as default, I don't have to choose from a list.   However, I know ubuntu is yet to be completely removed.  What steps do I take now to assure it is gone completely?

---

### Post by loserboy on 2007-06-29
you just need to delete the partition that ubutnu is on, so get partition magic or something and delete.

sorry to see you go, ya know it's healthy to learn new things

---

### Post by FuturePilot on 2007-06-29
Sorry to hear Linux didn't work out for you.
You'll need to boot the Live CD and start Gparted. Delete all of the partitions except your Windows partition. Then resize the Windows partition to take up the whole drive again

---

### Post by Syroco on 2007-06-29
To resize windows, can I use the Live CD?

---

### Post by Fireblend on 2007-06-29
Yes you can. Too used to exes? I didn't know people still used those xD The only think pulling me to Windows is Adobe software... :(
Edit: I'll actually try to pull you back, you sure you don't want an awesome looking desktop like the one in my sig? xD No virus, no horrible resource administration... keep the dual boot!

---

### Post by MCSE_Crossover on 2007-06-29
To ensure that it is gone completely, all you need to do is delete the partition that it was residing on. If you ran the "fixmbr" command, you have already rewritten the boot record.

To delete the partition, once in Windows, right click on your "My Computer" icon and click "manage". Once in the computer management window, under storage, click on "Disk Management"

You should see your partitions listed under there - one being your NTFS drive, your CD-Rom, and one labeled "unknown" or something. That one is your Linux partition. Just delete that (or all related 'unknowns') and reformat them as NTFS. This will create it as a new partition under your Windows installation.

Hope that helps. Sorry to see you go! I still use Windows quite a bit and have a lot of little quirks with Linux that are extremely frustrating...especially to my wife. But I overall think it just runs much better than Windows, I don't feel quilty about using pirated or illegal software under Linux, and it is inherantly more secure. Just a few points to think about before you leave! Give it a fair amount of time before you bail.

---

### Post by Syroco on 2007-06-29
I like Ubuntu, but installing programs is too much work than it should be. :(

I install regularly, and I just can't get used to it.

---

### Post by Fireblend on 2007-06-29
> **Syroco said:**
> I like Ubuntu, but installing programs is too much work than it should be. :(

I install regularly, and I just can't get used to it.

Use .debs!! They're exactly the same as setup.exe(s)!!! Have you done enough research?

Try installing anything from here, you'll see it's the same:
[http://www.getdeb.net/](http://www.getdeb.net/)

And once you've been using Ubuntu for a while, you'll realize that using the command line for 20 secs. is much better than spending 2 hours in the internet looking for software... There's also the Synaptic Package Manager and even the Add/Remove menu so you don't even have to touch the terminal! You can use debs for now, since they're the equivalent of Window's setup.exe

---

### Post by MCSE_Crossover on 2007-06-29
what do you mean by too much work? I think it is fairly simple...I mean, it is no double click and go. But with a .deb file, you right click and basically hit "install" or use "Add/Remove programs" or even "synaptic"

I understand "to each his own" but you should give it a shot. Are you new to Linux? I've been there and still am to a certain extent. But it gets easier as you use it. My problem was that Windows was always SOOOO easy to me and still is. Switching to Linux is like unlearning everything I have done for my whole life. But, on a positive side of Linux, I see it's possibilities. And in that, I think it is superior to Windows. It still has a ways to go until it is AS friendly as Windows for us Windows-users. But, it's free and legal!

---

### Post by Syroco on 2007-06-29
I couldn't figure out how to install Beryl or xgl!

I got way too flustered. :S

---

### Post by ajgreeny on 2007-06-29
Did you use **add/remove programs** or **synaptic,** or install many things the hard way with tarballs etc?  I find synaptic absolutely fantastic for everything I need with the exception of a few trusted .deb files I've used with sudo dpkg -i but that is similarly so easy to use that I'm surprised you have found things difficult.

Beryl is in the repos as well so all you need is to search in synaptic and click install.  Dead easy!

---

### Post by MCSE_Crossover on 2007-06-29
righto. Although installing programs in Windows is fairly easy and straight forward, FINDING the programs and then the associated updates is where it is really difficult. I guess there is pro's and con's on both OSes. But the thing I really like about Linux and the package management is that all installations, dependencies, updates, and drivers - for the most part - are all taken care of you. You install it once and then you never have to really worry about it again.

---

### Post by Fireblend on 2007-06-29
> **Syroco said:**
> I couldn't figure out how to install Beryl or xgl!

I got way too flustered. :S

Alright, I'll help you. Open up a terminal and type 

```
sudo apt-get install beryl
```

That's all! (Well, unless your graphic card is not compatible, which isn't Ubuntu's fault. Beryl is experimental software after all. If that's the case, try installing something stable, like amarok, just change where it says beryl in the code to amarok (an awesome music player!))

SUDO -> Gives you admin powers to change the system
APT-GET -> It's the "install/remove things" program
INSTALL-> tells the program you're gonna install a package
BERYL-> The name of the package

It's the same for every package! And as I said, use [http://www.getdeb.net/](http://www.getdeb.net/) for now, you'll get used to the terminal in no time! I was also afraid of it when I started :p but now it's like second nature :p

---

### Post by Syroco on 2007-06-29
> **MCSE_Crossover said:**
> To ensure that it is gone completely, all you need to do is delete the partition that it was residing on. If you ran the "fixmbr" command, you have already rewritten the boot record.

To delete the partition, once in Windows, right click on your "My Computer" icon and click "manage". Once in the computer management window, under storage, click on "Disk Management"

You should see your partitions listed under there - one being your NTFS drive, your CD-Rom, and one labeled "unknown" or something. That one is your Linux partition. Just delete that (or all related 'unknowns') and reformat them as NTFS. This will create it as a new partition under your Windows installation.

Hope that helps. Sorry to see you go! I still use Windows quite a bit and have a lot of little quirks with Linux that are extremely frustrating...especially to my wife. But I overall think it just runs much better than Windows, I don't feel quilty about using pirated or illegal software under Linux, and it is inherantly more secure. Just a few points to think about before you leave! Give it a fair amount of time before you bail.


This is what Disc Management looks like after I deleted the Unknown partitions.

[http://s14.photobucket.com/albums/a310/Syroco/?action=view&current=untitled.jpg](http://s14.photobucket.com/albums/a310/Syroco/?action=view&current=untitled.jpg)

Is that how it should be?

---

### Post by MCSE_Crossover on 2007-06-29
I really prefer to use "aptitude" vs "apt-get" as it handles removal better. See [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) for a greate explanatin of the difference between the two.

But for a new Linux user, I wouldn't worry so much about Beryl right now. You are just asking for problems that aren't needed until you really get a good handle on the basics of using the new operating system.. As stated, Beryl is still experimental and is known to cause a MANY issues with people.

---

### Post by MCSE_Crossover on 2007-06-29
I cant get to photobucket...can you just upload it in your post? Just click "attachments" when you are posting to the thread.

---

### Post by Fireblend on 2007-06-29
> **Syroco said:**
> This is what Disc Management looks like after I deleted the Unknown partitions.

[http://s14.photobucket.com/albums/a310/Syroco/?action=view&current=untitled.jpg](http://s14.photobucket.com/albums/a310/Syroco/?action=view&current=untitled.jpg)

Is that how it should be?

Yeah. it's gone :p

---

### Post by Syroco on 2007-06-29
Sorry, here.

---

### Post by MCSE_Crossover on 2007-06-29
Right. That is correct. Now, the green one is a logical drive. You can right click on that and hit delete as well. That will then add the 1.43GB to the unallocated 33.08GB. You can then right click on the roughly 35.5GB unallocated drive, and create another new NTFS partition to use within Windows if you like! :)

Hope that helps. Let me know if you have any other questions.

---

### Post by Syroco on 2007-06-29
> **MCSE_Crossover said:**
> Right. That is correct. Now, the green one is a logical drive. You can right click on that and hit delete as well. That will then add the 1.43GB to the unallocated 33.08GB. You can then right click on the roughly 35.5GB unallocated drive, and create another new NTFS partition to use within Windows if you like! :)

Hope that helps. Let me know if you have any other questions.

Would a new NTFS partition of 34.51GB drive improve Windows? XD

---

### Post by MCSE_Crossover on 2007-06-29
It wouldn't IMPROVE it, but it would give you some more space to save files and stuff. Right now you just have one large partition (C:) that is 114GB. You have used over half of it and you have EVERYTHING saved on it...unless you have an external drive. Creating that new partition would just give you an extra 35GB of storage to put files on or store backups on. If you don't, really, your just wasting your hard drive space. :)

Does that make sense?

---

### Post by stchman on 2007-06-29
> **Syroco said:**
> I like Ubuntu, but installing programs is too much work than it should be. :(

I install regularly, and I just can't get used to it.

I guess googling to find what you need, going to the website, downloading the program, and then installing the software is FAR easier than going to the Synaptic manager, highlighting what you want, then clicking apply.

I can see the difficulty.

---

### Post by MCSE_Crossover on 2007-06-29
**sniff, sniff** sarcasm?

---

