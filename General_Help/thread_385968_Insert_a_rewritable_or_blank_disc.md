---
title: "Insert a rewritable or blank disc"
date: 2007-03-16
forum: General Help
---

### Post by bbjimmy on 2007-03-16
I am trying to use the cd creator app and it keeps telling me to Insert a rewritable or blank disc when a blank disk is in the cd burner ... using Ununtu Edgy 6.10 and a Hewlett Packard CD-Writer plus 9100. I have had no trouble using this cd rw drive in any other OS. I had to copy my iso file to a Windows share and use Nero to write my xubunty install CD ( for a laptop ). Help.

---

### Post by bbjimmy on 2007-03-16
It's not the disk

I used the same cd, the same file, and the same CDRW and burned the CD. I booted into Zeta, mounted the Ubuntu disk, fired up cd burner and burned the iso using the same CD that ubuntu complained about. Any clues?

---

### Post by granny4linux on 2007-03-16
I've had similar problems when burning with nautilus. I've had success using k3b; I don't put the blank cd/dvd in until requested by the application.

---

### Post by bbjimmy on 2007-03-16
> **granny4linux said:**
> I've had similar problems when burning with nautilus. I've had success using k3b; I don't put the blank cd/dvd in until requested by the application.


What is k3b? I have never heard of it.

I am posting from my new xubuntu install on this old laptop. It sure beats Win2k for usability. 


I tried waiting until it requested a blank CD to insert one but it still kept asking.

---

### Post by holomorph on 2007-03-17
I was just having the same problem.  Found a solution here:
[http://www.ubuntuforums.org/showthread.php?t=12133](http://www.ubuntuforums.org/showthread.php?t=12133)

basically Start gconf and go to apps->nautilus-cd-burner and turn on burnproof and overburn (I tried just burn proof, and no luck, so it might just need overburn, perhaps for some reason it's not thinking the disk is big enough.  *shrug* )

---

### Post by holomorph on 2007-03-17
. . .  and it still doesn't work, though it will create the image now, but then when it tries to write to disk it still prompts me to insert a blank disk.  Time to install k3b or GraveMan or GnomeBaker I guess.

---

### Post by granny4linux on 2007-03-17
> **bbjimmy said:**
> What is k3b? I have never heard of it.

I am posting from my new xubuntu install on this old laptop. It sure beats Win2k for usability. 


I tried waiting until it requested a blank CD to insert one but it still kept asking.

bbjimmy:I hope the thread mentioned by holomorph re: nautilus helped you.


k3b is CD/DVD writing software; it's from KDE. I discovered it when I used Mandrake several years ago; it's a great program and I just like it. 

If you want to take a look at it, it should be available through Synaptic.

I think the more time you spend with XUbuntu the happier you will be and Windoze will just be a distant memory!!!

---

### Post by Muffy on 2007-03-28
I'm having the same problems too. I've tried tried both Nautilus and k3b, but they both still ask for a blank disc when there is already a blank disc in the drive. 

I've tried turning on the burnproof and overburn as suggested in the thread, but no luck. Any other ideas?

---

### Post by Muffy on 2007-03-28
Never mind, a trusty reboot fixed it.

---

### Post by Nipopolis on 2007-05-09
None of these fixes have worked for me either.  I downloaded Gnomebaker and was able to burn an iso image with no problems but right clicking on the iso and chosing "Write to disc" just will not work.  It keeps asking me to insert a disc.  I used gconf to update nautilus as described in other posts here but still nothing.  Hopefully, someone will find an answer.

Nip

---

### Post by granny4linux on 2007-05-10
Nipopolis, what version of Ubuntu are you using? I believe this problem is fixed in Feisty Fawn final release.

---

### Post by kelvin spratt on 2007-05-10
i use Fiesty burning Rewritables no problem this did occasionally happen in edgy cure manually blank disk
but not with KB3 it tell you it does not need blanking

---

### Post by Nipopolis on 2007-05-10
I just started using Ubuntu about a week ago and I have version 7.04 I believe.

Nip

---

### Post by kelvin spratt on 2007-05-10
fiesty should have no problem i burn rewritalbes every day insert disc wait for it to load close window right click on ISO 2nd entry from bottom of flag Write to disc you get asked if you want to erase media let it do the business I've burned 100 plus rewritables this way no problems but you may have a corrupted disc so then blank it manually this sometimes happens if it tries to burn but does not complete the process the burner then thinks the disc is raw a rejects it hope this helps

---

### Post by doughahn56 on 2007-05-16
great fix!
I turned on the 3 items mentioned above and wah-lah   burnage!
I dont use K3b (awesome) becuse I ended up with Gnome in ubuntu 7.4
I had to het <alt> <F2>  and type "gconf-editor" to bring up the configuration manager
then I cliced "apps" and scrolled down to "nautilus-cd-burner" opened it and there were the 3 check boxes for "burnproof" "debug" and "overburn"  I checked 'em all and closed the window 
and burned 400MB's of mp3's immediately
GREAT FIX

---

### Post by Nipopolis on 2007-05-16
I fixed mine also.  It took a little more work than using gconf but here it is.

1.  Go to Best Buy.
2.  Buy new cd/dvd drive.
3.  Install.

It worked perfectly right out of the box.  Maybe my HP 9100 was just too old but none of the fixes worked for me.  Thanks for your suggestions and help.

Nip

---

