---
title: "e2fsck crashes computer!"
date: 2008-04-11
forum: General Help
---

### Post by dreshden on 2008-04-11
Today, I was logged into Ubuntu 7.10 and I needed to get into Windows do some things. So I restarted the computer the normal way by pressing the button at the top right and selecting restart. Everything goes fine, I log into Windows, do what I need to do and restart the computer. Then I switch over to my external HDD with Ubuntu on it and it takes me straight to the command prompt for some reason. So i restart and it does the same thing for a couple of times. Then it starts to run fsck so I let it.

This is where the real problem starts.

After fsck gets about 30 to 40 percent done it stops and says that I need to run fsck manually. So I pop in my live CD and try to run fsck but it does not work. So I found this command: ```
 e2fsck -D -f /dev/sdb1
``` I did unmount my drive and it started to work but I had to sit there and hold down "y" because it kept going through differnt things about inodes. So after amount of time it starts going through things by itself. Then it starts to go through the inodes again but then it says something about copies, so again I have to hold down "y" by this time I put a weight on my keyboard and left for a bit. When I came back my whole computer was off. :(

I would just reinstall but I cannot access my home folder from the live CD so I cannot get any of my files from there. Is there a way I can make sure that it does not crash? Or is there an easier way to fix this with out using e2fsck? Thanks in advance.

---

### Post by mrsteveman1 on 2008-04-11
You don't have to hold down Y you can tell fsck to answer yes to every question, but i don't think you should do that unless something is really wrong with the filesystem.

If the filesystem suddenly got all these errors it could be the disk itself, you should probably use something like hdat2 to check the drive and try to repair any bad sectors.

I've seen fsck act weird before though, so its hard to say whats wrong.

Why don't you check the kernel log and see if there are any hardware errors (use dmesg). Also you might want to run smartctl on the drive (i think its the -A or -a flag) to see if there are any errors.

---

### Post by dreshden on 2008-04-12
Ok thanks for the help mrsteveman1 but nothing seemed to work. :( for hdat2 my live cd said that the command was not found. When I typed in dmesg it gave me a list full of stuff that got cut off at the top and i have no idea what it all means. For smartctl it gave me an error when I ran it 

"ubuntu@ubuntu:~$ smartctl --all /dev/sdb1
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       2500BEA External Version: 1.04
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options."

Finally i found that i can run e2fsck -cc and it will supposedly do a check on all the blocks on my hard drive. That took over 12 hours and it finally finished and it asked to clear some random inodes then it restarted e2fsck and started the whole process over again :(

So I logged back into Windows cause I have nothing else to do and I see that my Ubuntu drive is mounted in Windows and I can look at the files. When I click on the home folder to try and recover my files it says that it is corrupted :( This is the same for the media and tmp folder on my Ubuntu drive. Is there any other way that I can fix this problem with out reinstalling?

---

### Post by mrsteveman1 on 2008-04-13
hdat2 is a dos app, its not on the ubuntu CD. This sort of thing can't be done from inside linux as far as i know.

You can use it by downloading UBCD from here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Its in one of the menus for hard disk tools. It should be able to tell you if the drive has smart errors, and if any of the blocks on the disk are bad. Thats the first place to check as far as I'm concerned, because ext3 shouldn't randomly corrupt itself.

---

### Post by dreshden on 2008-04-14
Ok I made the CD and I went to that hard drive tools to try and find the right tool but there are so many and I have no idea which one would be the one to use to find the errors. I tried a couple that I thought might work but I do not know any of the commands for them. It would be great if you can tell me a tool or two on the cd that might be able to help me with this.

Thanks again mrsteveman :D

---

### Post by mrsteveman1 on 2008-04-14
Definitely use HDAT2, i don't have a cd burned at the moment but i looked at the menu files, and its supposed to be in hard disk tools > diagnostic tools > hdat2

Once you have it running it gives you a lot of options, select your drive, then check under the S.M.A.R.T menu and run the short self test, it should also be telling you if anything is wrong that it already detected.

When that is done, go to drive level tests, and select check and repair bad sectors. It might take a while but it will find any problems on the drive, tell you about them, and try to fix them.

If there are a lot of errors you should replace the disk for sure, but it should still be possible to get the data off if that happens.

---

### Post by dreshden on 2008-04-15
Ok, this is weird, today when I logged into windows I looked at My Computer and there was my external HDD. I click on it then on my home folder and it is not corrupt anymore. I was very happy and started to copy a bunch of files to my windows drive. After I was done, with everything I needed to do I restarted and booted to my external HDD. It told me that I need to run fsck manually so I did and it went through everything fine. So I restarted again and got to the Ubuntu Log in screen. I was really happy at this point so I type in my username and password and hit enter. Then it just sits there with a blank screen. :( I am thinking about just coping all the important files and reinstalling Ubuntu again. Unless you know of an easier way that I can fix this with out any reinstalling. Thanks again mrsteveman!

---

### Post by mrsteveman1 on 2008-04-16
Sounds like something is wrong with one of the files involved in startup, which is possible if the filesystem was corrupt or a block on the drive failed.

Definitely get your important stuff off, and run those HDAT2 checks (check and repair bad sectors), if it says the drive is ok just reinstall ubuntu. If it finds a bunch of bad blocks get a new disk.

---

### Post by dreshden on 2008-04-16
Ok, I went to reinstall ubuntu and it showed that my drive only has 9GB when it is suppose to have 250GB. So does this mean that the physical drive is broken?

I would run hdat2 but for some reason it wont recognize my drive when i click no drives, but when i click on USB drivers it turns off my keyboard and mouse so i cant do anything. not sure what to do there.

---

