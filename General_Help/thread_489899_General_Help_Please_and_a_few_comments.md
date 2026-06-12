---
title: "General Help Please and a few comments"
date: 2007-07-01
forum: General Help
---

### Post by flyingdoctor on 2007-07-01
Guys,

hope you wont mind me posting here and asking for some advice and making a few observations.

Gotta give you a bit of background first.

I'm a crusty old buffer who's been around computers for quite a while. Started off on the old Commodore Pets then the Sinclair Spectrum and Amstrad 664 a million years ago back in Ireland. Learned Z80 code so I could break protection systems and get infinite lives on things like Manic Miner and Jet Set Willy:p. Got pretty darned good at it too. Moved on to leasing a LINUX based server a few years ago to host webpages I made. Bloody difficult and frustrating at the start but made out OK thanks to a couple of the great books that are out there. Changed the hosting service 2 years ago and now they have everything installed or do any mods for me. Been trying to get away from Bill's death grip for a while and when I saw that Dell was shipping PCs with UBUNTU I thought maybe it was ready for primetime. The fact that I could run some of my old stalwarts like Eudora and Turbonavigator under Wine sold me so I downloaded the PC LINUX OS ISO. I had an older Dell notebook which I had a spare 10 Gig drive for so I swapped it out, formatted it and installed PC LINUX OS. Went very well except for a few glitches which I sorted out. Seemed to be running ok but after a couple of problem boots I began to suspect I was doing something wrong. The boot failed and I found Grub and had a play with that. No dice so I gave up. The drive was making a few odd sounds so I suspected it had seen better days and that may have been the problem. Tossed it and put in a 30 Gig I had. Decided that maybe Dell was right and UBUNTU was the way to go to went with 7.04. Installed in a breeze. Set everything up and changed background and theme, installed Krusader which I prefer, and set about trying to tart the system. Hello problems. RAR files can't be opened. I was sure that Krusader was supposed to support RAR. Nothing else seems to. Of course I was doing all this stuff through Firefox and downloading packages. Hmmmmm, what package? Tar, Deb, RPM????? RPM was a non started so I found Alien. Crikey, command line stuff now. Nightmare, as I'd forgotten most of my command line stuff and the great Linux books were in a box somewhere. Next problem was that I had a usb2 hard drive which UBUNTU would read from nicely but not write to. Finally sussed that it was because it was a NTFS format. OK I can fix that with NTFS configuration tool. Did the business, still wouldn't write. Unplugged the drive and got a big fat "shouldn't have done that" message. Plugged it back in and I got a "cant mount" message. Trawled around and found that I need NTFS fix. Finally found it and it is in a a compilation which is an RPM distribution. Tried Alien. Got nowhere. It was in a directory called Downloads and when Alien ran I ended up with a directory Downloads$ I think, but nothing in it. I then trawled around the help and found the "how to install anything in UBUNTU" page. Nice, but after trying a few things including Synaptic I'm still stuck. 

So here are the comments after 2 days of playing.

UBUNTU is tremendous. Straight out of the box it found everything on my Dell laptop. CD Drive, USB pen drive and USB Hard drive. I was impressed. Installing packages using Synaptic and the Add / Remove is pretty darn neat especially with Broadband. Where it falls over is it will find stuff in a repository and a CD but not on the hard drive or anything plugged in. Maybe I'm doing something wrong but surely to be able to search the mounted drives is a no brainer. I can't see why I need to put stuff on a CD to be able to install it.

I still can't get UBUNTU to open RAR files and I have no idea how to deal with ISO files or burn CDs or DVDs. I must admit I didn't try to hard as it was bottom of the list.

My USB hard Drive is totally stuffed for UBUNTU as I cannot install NTFSfix. I admit defeat.

My feeling is that I can't see Dell selling many UBUNTU rigs and in a year they will probably discontinue. Why? Just too different for the average Joe who uses or is used to Windows at the office. I feel that people like us won't buy a preloaded PC, we'll just download the ISO and do everything ourselves. Much as I wish it was, I just don't think LINUX is for the man in the street. Heck, that pains me to say it, too.

So I'll keep playing with the system to see if I can fix the NTFS drive and try to find RAR packages or a burner which handles ISO files. I'll probably have a play with Wine if I can install it and see what happens. Ultimately unless I get to grips with it quickly I'm afraid it is format and back to Windows... now that hurts especially as I thought I saw a bit of light out there.

Thanks for letting me rambling and if anyone has any ideas to solve the RAR, ISO and NTFS probs I have, I'd be very grateful.

Pete

---

### Post by jwh400 on 2007-07-01
For opening rar's I use XArchive which is in the repositories. Also there you will find GnomeBaker which is a simple and straight forward CD/DVD burner that will burn iso files.

---

### Post by flyingdoctor on 2007-07-01
> **jwh400 said:**
> For opening rar's I use XArchive which is in the repositories. Also there you will find GnomeBaker which is a simple and straight forward CD/DVD burner that will burn iso files.

Many thanks. I'll head on over there right now :-)

Pete

---

### Post by flyingdoctor on 2007-07-01
Gnomebaker looks great but Xarchive falls over with RARs too...this file type not supported..... the proper archiver is not installed.

Not sure what that means.

Pete

OK it seems like wrappers are missing. rar-wrap.sh and a few others.

---

### Post by jwh400 on 2007-07-02
This post from koskon may help you.

[http://ubuntuforums.org/showpost.php?p=2920934&postcount=4](http://ubuntuforums.org/showpost.php?p=2920934&postcount=4)

---

### Post by Rossiter on 2007-07-13
Just to address the issue of .iso files...
I found that Ubuntu, freshly installed, handles them quite easily.  Just right click on the .iso file and select "_W_rite to disk...".  A few minutes later you'll have a working CD.  I've been kept quite busy burning my dowloaded Ubuntu image file to disks for all of my friends.

---

