---
title: "Blank media not recognized..."
date: 2007-10-13
forum: General Help
---

### Post by Maddmaxx on 2007-10-13
I apologize in advance if I have repeated a thread, but after trying any and all fixes already available on this forum and have not fixed the issue. When I first installed Ubuntu 7.04 on my IBM P4 2.4, I was able to burn cd's and dvd's no problem. It must have been an upgrade or something but for the last few months and a lot of reading I still can not burn anything. I have swapped burners with my xp system and either burner works in that system (Sony DRU-710A, and Lite On LH-20A1H both on latest firmwares). From what I can tell it is because the drive is being recognized as a SCSI device and not an IDE device (scd1 instead of what it used to list as which I can't remember). If I insert a blank cd or dvd it used to ask me what to do with it, now there's no popup and if I use k3b or Brasero and add files to the disc and press "Burn" it tells me to put a blank disc in the drive, well there's already one in there...There have been a few fixes posted, but none of the ones I've tried have done anything to make it start to work. If anyone has found a fix for this issue, your help would be greatly appreciated! 

Thank you in advance!

---

### Post by Maddmaxx on 2007-10-20
Well I'm now fully upgraded to 7.10 Gutsy Gibbon and I still have the issue, Both drives work in windows but neither of them in Ubuntu, any ideas?

---

### Post by starfry on 2007-10-23
I have a similar issue too. I started a thread for it.

[http://ubuntuforums.org/showthread.php?t=587263](http://ubuntuforums.org/showthread.php?t=587263)


Basically, I can read DVDs fine. I wrote one DVD succesfully. However, now when I put a blank DVD in the drive, the stops being recognised and I experience the symptoms you describe. I can no longer see the drive and I can't eject it. The only way to get the blank disc out is to reboot.

After rebooting it works again until I insert another blank dvd.

Here are my device nodes:

% ls -l /dev/hd{c,d}*
brw-rw---- 1 root cdrom 22, 0 2007-10-22 23:27 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2007-10-22 23:27 /dev/hdd
% ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/cdrw -> hdd
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/dvd -> hdc
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/dvdrw -> hdc

(this is on 7.04 Ubuntu Feisty)

---

### Post by Maddmaxx on 2007-10-26
I'm not sure, but I don't think our problems are related. I've never had a problem ejecting the drive, and I've never been able to read or write ANY disks in EITHER of my drives, that's 4 drives, 2 burners and 2 roms. The problem I am dealing with has been due to the drive being recognized as a SCSI device and not a standard IDE device... I'd like to be able to resolve this issue as I have not been able to burn disks since the release of7.04 and I'm running 7.10 now. Any help?

---

### Post by starfry on 2007-10-30
Our problems aren't related. 

I discovered my XP had the same problem, which lead me to suspect the drive. I patched the firmware and that sorted it. Looks good so far...

---

### Post by Maddmaxx on 2007-10-30
UPDATE: So I went to the local computer store and asked if they could test my drives, the Sony drive and the Lite-on drive are both shot... So I buy a new one and put it in my Ubuntu 7.10 computer and burned about 4 discs successfully and now it just quit working again... Same thing, put a blank disk in and press "Burn" up comes a popup saying "Insert a blank disc" BUT THERE IS ONE IN THERE!! So I take the drive back to the store, they say it must be faulty, and replace it for warranty, bring the new one back and I put it in my Windows computer, at least now I can burn in Windows.  It's obvious that Ubuntu is doing something to render these drive useless! I've cooked 3 DVD burners with this OS... If I install the drive in Ubuntu and use it for the 3-4 burns it does, when it quits, I put the drive back into the windows system and it does not read anything or write anything, in fact I put a bought copy of Star Wars in the drive and it would not show up that there is a disc in the drive. So the closest I am to fixing the problem is replacing the drive every couple of days, but the store is starting to get a little suspicious, since there are only 2 locations locally. I thought it may be my hardware, but i have switched the drives from primary to secondary IDE channel and it's only the optical drives that are acting up. I thought it could be the cables, so all of my IDE cables are brand new... I'm at a loss, won't somebody please help me???

---

### Post by Maddmaxx on 2007-11-20
bump\

---

### Post by GreenMeanie on 2007-11-20
I can burn a CD but not a DVD and I know my burner works.

---

### Post by GreenMeanie on 2007-11-22
come on don't make us use windows ;)

---

### Post by dragonslave02 on 2007-12-07
I have tried everything I could think of and have read nothing works I used Nero, k3b, gnomebraker, i tried with dma on and off, different DVD+R bands, I know that it works and with the dvd's that i am using because i was able to make a copy of the live cd for gusty that i gave to my brother to use but i can not seem to get it now to see the blank media that i put into to burn to it does say when i put one in that you have inserted a blank dvd+r would you like to create a dvd please tell me what is wrong with it

oh yeah i can burn cd's just fine

---

### Post by misha1983 on 2007-12-29
I have a SONY DRU-710A and am having the same problem.

I'm able to read a CD using that drive, but when writing, I get this message from cdrecord:  "cdrecord: No disk / Wrong disk!"

This DVD drive worked fine under FC6.

Were you able to find a solution to your problem?  

Cheers,
Michael

---

### Post by misha1983 on 2007-12-30
I was able to salvage a Windows box and try to DRU-710A in it.  It can read CDs and DVDs, but cannot write.  For now, I'm assuming something happened with the device in the days since I've installed Ubuntu, since the last thing I did before installing it was burn a backup DVD of my /home.

I managed to find an old LITE-ON LTR-40125W drive lying around which I will use for CD burning in the meanwhile.  It works fine for now. Might have to purchase a new DVD burner in the long run.

Cheers,
Misha

---

### Post by Zimmer on 2007-12-30
Been having similar issues with a Sony unit I got from a friend some months back.Worked ok , burned DVDs and CDRs.
Started not recognising blank CD-Rs last month... (Dapper 6.06 user BTW)

So I bought a new one yesterday (NEC Optiarc 7200) and have spent the best part of 10 hours installing and re installing drives!! testing and reading forums on similar issues..
The link below has been active since around May 2007..no real resolution either.
[http://club.cdfreaks.com/f86/nec-optiarc-dvd-r-reading-problems-209168/](http://club.cdfreaks.com/f86/nec-optiarc-dvd-r-reading-problems-209168/)

The new NEC Optiarc 7200 recognises all disks as writeable blank media. So I cannot play audio cds or DVDs.
It did, however, boot a Knoppix live CD.. hmm.. so has something changed with a recent kernel / module upgrade? 
I have resorted to my original (4 year old) CD writer ..
The NEC drive goes back tomorrow and I will try and purchase a Pioneer 112.
Unless, of course, someone would care to tell me that is not a good idea...

EDIT:  Have a Pioneer 115 now, installed, working straight away....

---

