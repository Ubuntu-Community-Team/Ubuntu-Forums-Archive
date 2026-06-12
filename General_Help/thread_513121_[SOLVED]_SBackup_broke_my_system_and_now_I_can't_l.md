---
title: "[SOLVED] SBackup broke my system and now I can't log in (posting from Windows :-("
date: 2007-07-30
forum: General Help
---

### Post by startling on 2007-07-30
I just tried using Simple Backup for the first time and found it far from simple. In fact, I found it awkward.

Firstly, I thought there was an error. After I pressed 'backup now' a dialog appeared stating "A backup run is initiated in the background. The process id is: 7740." I did not know whether this was an error message, or whether it meant that I had to wait because backups are started later 'in the background'. Quite confusing at first, though I now realise what that message meant.

A suggestion: please consider re-wording that dialog so that it states: "A backup run **has been **initiated in the background..." This would be much more clear and would tell the novice user that something *has been done*. (Ideally all sorts of feedback would be much better - status bars, warnings, etc. On my Windows machine I used an application called Acronis True Image and that was very simple to use and had lots of feedback for the user.)

<gentle humour> Alternative suggestion: change the name from "Simple Backup" to "Somewhat Difficult Backup" </gentle humour>

Next, I found that my hard disk was suddenly full. Simple Backup had eaten my drive without warning me that it was going to do so. Scary.  I then had to learn new things: running Nautilus as root, and finding the backup file. Then, when I right-clicked on it, there was no option to delete (I can see why this would be, as a safety precaution) so I sent it to trash, but then, of course, my disk was still full so I had to find root trash and press the delete key (no option to delete on right-click again, which, considering I'm already in Trash seems a bit odd).

I don't want to use Simple Backup again, to be honest, until it has become more user-friendly. For example, it would be nice to know in advance the size of the backup it was going to write. Should I just manually back up files for now (which seems tedious and silly in a modern world) or do you have any other suggestions?

On a positive note, I still much prefer Ubuntu to Windows.

---

### Post by startling on 2007-07-30
I desperately need to send an email but cannot log into Ubuntu because of this problem. (I've had to boot into Vista to post this.) I'd be very grateful for any help.

Simple Backup, without asking me, completely filled my hard disk. So I sudo'd into Nautilus as root and removed the offending backup file to trash and then deleted it from root trash by pressing the delete key. Upon quitting Nautilus as root I noticed that the console from which I had sudo'd Nautilus had the following error message:

[INDENT](nautilus:8018 ): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

--- Hash table keys for warning below:
--> file:///root/.Trash


(nautilus:8018 ): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)[/INDENT]


I must say I'm really disappointed that a Backup program can do so much damage to a system.

---

### Post by startling on 2007-07-30
One other thing I forgot to mention in my previous post: 

I tried booting from the recovery kernel option in Grub and when it got to the command line, the line before it said something like "mount* warning: no end newline in /etc/fstab" I'm sorry, that's from memory because obviously I'm booted in Windows trying to get this sorted out asap.

---

### Post by startling on 2007-07-30
Sorry to keep replying to my own post but I've remembered something else: I noticed in Nautilus that disk space was being shown as zero so I deleted loads of stuff, but it still kept showing disk space as zero.

I desperately need to get Ubuntu up and running soon because I'm using it for work and need to get something emailed to a customer asap.

---

### Post by startling on 2007-07-30
*PLEASE* help! Anybody? Any ideas? Is this a major problem? Do I need to delete Ubuntu and start again?

---

### Post by dando80 on 2007-07-30
What exactly is happening? How far are you getting in the boot process?

---

### Post by startling on 2007-07-30
Hi Dando80. Thanks for your reply.

It gets as far as asking me for my user name and password then tells me it cannot go any further. I think it's to do with the disk being reported as full, even though it shouldn't be.

---

### Post by dando80 on 2007-07-30
If you Alt-Fkey to a virtual terminal and log in, what does df say about the root fs?

---

### Post by startling on 2007-07-30
> **dando80 said:**
> If you Alt-Fkey to a virtual terminal and log in, what does df say about the root fs?

I'm sorry. I'm afraid I don't understand that. I'm new to Ubuntu. How do I AltFkey to a virtual terminal, please? And what is df? Thanks.

---

### Post by dando80 on 2007-07-30
There are by default seven virtual terminals. The xserver usually takes up number seven. If you hit the Ctrl-Alt key at the same time as one of the Function keys from F1 to F6, it will take you to the corresponding virtual terminal, where you can log in and type "df" (without quotes), and <Enter>. This will show you the usage on your file systems. 

E.g.

dan@hyrule:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/mapper/sdc3       3099292   1256896   1684960  43% /
varrun                 1029860       296   1029564   1% /var/run
varlock                1029860         4   1029856   1% /var/lock
procbususb             1029860       344   1029516   1% /proc/bus/usb
udev                   1029860       344   1029516   1% /dev
devshm                 1029860         0   1029860   0% /dev/shm
/dev/mapper/sdc1        150525    103146     39349  73% /boot
/dev/mapper/sdc8       5162796   1757432   3143108  36% /opt
/dev/mapper/sdc7       9290808   7296232   1522720  83% /usr
/dev/mapper/sdc6       3099260   3027708         0 100% /var
/dev/mapper/sda10    117136892  21666604  95470288  19% /mnt/recordings
/dev/mapper/sda11    180061224  54280228 116634392  32% /mnt/stuff
/dev/mapper/vg1-home 194039284 108602788  75579884  59% /home
/dev/mapper/vg1-movies
                      27867324   7795692  18656056  30% /mnt/movies
dan@hyrule:~$ 

If / is too high, it is a problem.

You can get back to the gui by hitting Ctrl-Alt F7

---

### Post by startling on 2007-07-30
I'm posting this from Windows because I cannot log into Ubuntu at all, so I cannot get to a terminal at present. As I say, I think it's a problem with Ubuntu thinking the disk is full, when it shouldn't be. Though I don't understand it, I think this warning is a clue to the problem:

"nautilus-metafile.c: metafiles" hash table still has 1 element at quit time

---

### Post by startling on 2007-07-30
The problem caused by Simple Backup is much worse than I had initially thought. Because it ate my disk, and I had to delete the backup file so that I had any disk space at all (surely a backup routine should be configured to leave at least ***some ***disk space?) the terminal that I sudo'd nautilus from reported a warning when I closed the sudo nautilus window. It said:

[INDENT]Hash table keys for warning below:
--> file:///root/.Trash

(nautilus:8018 ): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)[/INDENT]

I then found to my horror that Ubuntu was still reporting my disk as full (0 bytes free). Naturally no applications would work without disk space so I deleted a load of files. **Still **Ubuntu said it had no disk space. So I tried a reboot, and that made it worse. After entering my user name and password a dialog said that it could not continue. 

I am frankly amazed that Simple Backup should be configured by default to eat all available disk space without any warnings whatsoever.

I cannot get into Ubuntu to do some vital and urgent work. I have booted into Windows to post this. Any help would be gratefully received.

---

### Post by AtrejuT on 2007-07-30
try the following (I don't know if it will help, though):

boot into an ubuntu recovery mode (should be listed in your grub boot menu)

in a console type
```

cd /root/.trash
rm *

```

if you can't find the recovery mode just boot up your ubuntu as always but don't try to log on at the graphical screen. instead press ctrl+alt+f1. this should get you to a console where you can log in and type the above commands (prefix with sudo)

---

### Post by asmoore82 on 2007-07-30
err... suggestions on howto improve SimpleBackup should go to SimpleBackup ...
[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

if you are still out of disk space, make sure to "empty" all trash cans, yours and root's if you deleted things graphically as root ...

(you may have to [ctrl]+[alt]+[f1] at the login screen to go non-graphical)

login non-graphical -OR- get a failsafe Term session and ...

```
~ $ rm -rf $HOME/.Trash/*
~ $ sudo rm -rf /root/.Trash/*
```

---

### Post by startling on 2007-07-30
> **AtrejuT said:**
> try the following (I don't know if it will help, though):

boot into an ubuntu recovery mode (should be listed in your grub boot menu)

in a console type
```

cd /root/.trash
rm *

```



Many thanks for your help but it said there's no such directory. I typed dir and the only file or folder was 'desktop'.

---

### Post by sacherjj on 2007-07-30
Sometimes it is easy to miss the directories that start with periods.  Use ls -a to show everything, including these directories.

---

### Post by startling on 2007-07-30
> **asmoore82 said:**
> err... suggestions on howto improve SimpleBackup should go to SimpleBackup ...
[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

Thanks!

> **asmoore82 said:**
> if you are still out of disk space, make sure to "empty" all trash cans, yours and root's if you deleted things graphically as root ...

(you may have to [ctrl]+[alt]+[f1] at the login screen to go non-graphical)

login non-graphical -OR- get a failsafe Term session and ...

```
~ $ rm -rf $HOME/.Trash/*
~ $ sudo rm -rf /root/.Trash/*
```

I found my Ubuntu CD and have booted from that. 

I did a sudo su at a Terminal and I navigated to my Ubuntu disk, by typing 'cd /media/disk/root' and the prompt showed I was there. I then typed 'cd /.Trash' and it said: 'bash: cd: /.Trash: No such file or directory' even though when I use graphical Nautilus I can clearly see it there! (I must stop gnashing my teeth - I have to see my dentist tomorrow!)

Please can you advise me? I'm tearing my hair out.

---

### Post by AtrejuT on 2007-07-30
can you (from the console again) type

```

du
df

```
and post the output?

btw, there was a typo in my first post, it should have been .Trash, but you checked that later anyways

---

### Post by startling on 2007-07-30
Getting somewhere. I finally logged onto my trash folder (I was typing 'cd /.Trash' rather than 'cd .Trash' which worked - argh!) Anyway, here's what happened next:

```

root@ubuntu:/media/disk/root/.Trash# rm *
rm: cannot remove `2007-07-30_08.03.00.025250.mark-laptop.ful': Is a directory
root@ubuntu:/media/disk/root/.Trash# cd 2007-07-30_08.03.00.025250.mark-laptop.ful
root@ubuntu:/media/disk/root/.Trash/2007-07-30_08.03.00.025250.mark-laptop.ful# rm *
root@ubuntu:/media/disk/root/.Trash/2007-07-30_08.03.00.025250.mark-laptop.ful# cd ..
root@ubuntu:/media/disk/root/.Trash# rmdir 2007-07-30_08.03.00.025250.mark-laptop.ful
root@ubuntu:/media/disk/root/.Trash# ls -a
.  .. 

```

I'm going to try a reboot now...

---

### Post by startling on 2007-07-30
> **AtrejuT said:**
> can you (from the console again) type

```

du
df

```
and post the output?

btw, there was a typo in my first post, it should have been .Trash, but you checked that later anyways

here's the output:
```

root@ubuntu:/media/disk/root/.Trash# du
4       .
root@ubuntu:/media/disk/root/.Trash# df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   513036     33788    479248   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   513036     33788    479248   7% /lib/modules/2.6.20-15-generic/volatile
varrun                  513036       112    512924   1% /var/run
varlock                 513036         0    513036   0% /var/lock
udev                    513036       120    512916   1% /dev
devshm                  513036         0    513036   0% /dev/shm
tmpfs                   513036        12    513024   1% /tmp
/dev/sda5             17615120  17601572         0 100% /media/disk
root@ubuntu:/media/disk/root/.Trash# 

```

Thanks for your help

---

### Post by startling on 2007-07-30
I'm still worried. Even though I have finally actually deleted the contents of my root trash (I think!) Nautilus is ***still reporting*** 'Free space: 0 bytes'. Argh! and Argh! again. I daren't reboot.

---

### Post by AtrejuT on 2007-07-30
ok so you have to do the du in /dev/sda5 (which is indeed as full as it can be as can be seen from the second command)

```

cd /media/disk
df

```

---

### Post by startling on 2007-07-30
> **AtrejuT said:**
> ok so you have to do the du in /dev/sda5 (which is indeed as full as it can be as can be seen from the second command)

```

cd /media/disk
df

```

I did a du at the /media/disk prompt which then went on for ages. When it finally stopped (you can see the tail end below) I did a df, and the output is posted below:

```

16      ./root/.gconf/apps/gedit-2/preferences
20      ./root/.gconf/apps/gedit-2
52      ./root/.gconf/apps
56      ./root/.gconf
512     ./root
4       ./initrd
6364    ./sbin
4       ./opt
17425392        .
root@ubuntu:/media/disk# df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   513036     33788    479248   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   513036     33788    479248   7% /lib/modules/2.6.20-15-generic/volatile
varrun                  513036       112    512924   1% /var/run
varlock                 513036         0    513036   0% /var/lock
udev                    513036       120    512916   1% /dev
devshm                  513036         0    513036   0% /dev/shm
tmpfs                   513036        12    513024   1% /tmp
/dev/sda5             17615120  17601572         0 100% /media/disk
root@ubuntu:/media/disk# 

```

---

### Post by AtrejuT on 2007-07-30
yeah I see. You can somehow tell du just to give you a summary for the top level directories, not for each subdirectory. I don't know how though, and I'm not at home right now, so I don't have ubuntu around to check.
but maybe you can find that out yourself by typing
```

man du

```

which should give you a help page listing options for du. You can leave the help browser by just typing 'q' (without the quotation marks)

---

### Post by asmoore82 on 2007-07-30
okay, root's trash is emptied, how's about your trash ?

and BTW in terminals the TAB key is your best friend...

```
~ $ cd /media/disk/home/*<your user name>*/.Trash/
.Trash $ ls -a
.Trash $ rm -rf *
```
Real Keystrokes: cd[space]/media/disk/h[tab][tab].T[tab] ... :D

---

### Post by Gen2ly on 2007-07-30
```
[email]root@ubuntu:/media/disk/root/.Tras[/email]h# rm *
rm: cannot remove `2007-07-30_08.03.00.025250.mark-laptop.ful': Is a directory
```

Looks like a directory still is in [FONT="Fixedsys"]/root/.Trash[/FONT] you'll need to use the flag for recursive [FONT="Fixedsys"]rm -r *[/FONT]

---

### Post by startling on 2007-07-30
> **asmoore82 said:**
> okay, root's trash is emptied, how's about your trash ?

and BTW in terminals the TAB key is your best friend...


Thanks for the tab tip! That's so much quicker! 

Okay, my trash is empty now. But **still** Nautilus is showing 'Free Space: 0 bytes'  :-(

This doesn't look good, does it?

Thanks for your help asmoore82 - it's really appreciated.

---

### Post by startling on 2007-07-30
> **Dirk.R.Gently said:**
> ```
[email]root@ubuntu:/media/disk/root/.Tras[/email]h# rm *
rm: cannot remove `2007-07-30_08.03.00.025250.mark-laptop.ful': Is a directory
```

Looks like a directory still is in [FONT="Fixedsys"]/root/.Trash[/FONT] you'll need to use the flag for recursive [FONT="Fixedsys"]rm -r *[/FONT]

Thanks for your post. I did empty root the long way... But I'll know better next time! :-) 

Actually it wasn't a directory - it was a zipped file of a backup which started this whole mess in the first place. I wonder if that had anything to do with Nautilus being naughty originally?

I'm really worried that it looks like something's seriously broken with this disk now. The warning about hash tables didn't look too healthy... :-(

---

### Post by startling on 2007-07-30
Update: I found my Ubuntu CD and booted from that. I manually deleted the several Gigabytes that remained in the root trash (even though Nautilus stated that it was empty - sigh) but still the disk is ***still*** reporting **Free Space: 0 bytes** !

I'm almost at my wit's end. Does anyone know whether I should just delete Ubuntu? Or is this a fixable thing?

Is it to do with the hash tables mentioned in the original warning output?
```
(nautilus:8018 ): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time 
```


In case anyone's following this thread, there's more to it here:

[http://ubuntuforums.org/showthread.php?t=513074]("http://ubuntuforums.org/showthread.php?t=513074")

I had posted a suggestion regarding SBackup there.

---

### Post by startling on 2007-07-30
This, however, is wrong. The disk *was* full but I deleted several gigabytes' worth of files and yet still it reports Free Space: 0 bytes.

Is there any way to repair this? Any way for the disk to re-read all its contents and build its tables again? Apologies for my terminology but I am new to Ubuntu. (In Windows I would run checkdisk but I'm not sure what to do with Ubuntu.)
 
After I had deleted some files in a sudo Nautilus session the Terminal reported this warning:
```

--- Hash table keys for warning below:
--> file:///root/.Trash

(nautilus:8018 ): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)

```

I have spent a whole day not working because of this problem (which means I have earned nothing today - ouch!) so I am desperate to resolve this issue one way or another soon (though I'd hate to go back to Vista!).

Would re-installing Ubuntu work? (It would take days to get things back to how they were before so if there's a way without doing that, it'd be great.)

---

### Post by fjgaude on 2007-07-30
You can run fsck /dev/sda from an unmounted /sda or from a live CD. I don't think I'd run it from a mounted partition.

Also make sure with your deletes that they aren't still in the Trash. <smile>

fsck does what chkdsk does in Windows.

frank

---

### Post by startling on 2007-07-30
I ran fsck /dev/sda5 but when I just checked in Nautilus it is **still** reporting Free Space: 0 bytes

I cannot tell you how depressed I am.

---

### Post by Maxtorm on 2007-07-30
A few things:
[LIST=1]
[*] You're sure that sda5 is the same device you're having the problem on?
[*]What does ```
df -h
``` return (from a terminal session)?
[*]Have you tried explicitly removing the root Trash folder?  That is, ```
sudo rm -r /root/.Trash/*
```
[*]Since you can access Nautilus, does the Disk Space Analyzer (under Application -> Accessories I believe) indicate that the /root/.Trash folder is the problem?[/LIST]

---

### Post by bodhi.zazen on 2007-07-30
> **startling said:**
> *PLEASE* help! Anybody? Any ideas? Is this a major problem? Do I need to delete Ubuntu and start again?

Startling : I merged your three threads.

Please do not start multiple threads on the same subject:

1. It leads to a duplication of effort from those trying to help.

2. It is difficult to help as now you have information across multiple threads ...


Also, please do not bump your own threads.

1. We are all volunteers here ...

2. We have an unanswered team (to help with more difficult problems), but they can not detect you need assistance if you keep bumping your thread ...

My advice to you is that you need to delete files. You need to find them.

Search you home directory, search your trash. Use Nautilus and show hidden files. Use du ...

---

### Post by startling on 2007-07-30
> **Maxtorm said:**
> A few things:
 You're sure that sda5 is the same device you're having the problem on?


Yep.

> What does ```
df -h
``` return (from a terminal session)?


/dev/sda5                 17G      17G        0    100%    /media/disk

> Have you tried explicitly removing the root Trash folder?  That is, ```
sudo rm -r /root/.Trash/*
```


Yes. Here's output:
```
root@ubuntu:/media/disk/root# ls -a
.          .bash_history   Desktop    .gnome2          .recently-used.xbel
..         .bashrc         .esd_auth  .gnome2_private  .synaptic
.aptitude  .cairo-clockrc  .gconf     .nautilus        .Trash
.azureus   .config         .gconfd    .profile         .wapi
root@ubuntu:/media/disk/root# rm -r /media/disk/root/.Trash/*
rm: cannot remove `/media/disk/root/.Trash/*': No such file or directory
root@ubuntu:/media/disk/root# 
```


> Since you can access Nautilus, does the Disk Space Analyzer (under Application -> Accessories I believe) indicate that the /root/.Trash folder is the problem?


Strange. Disk Space Analyzer reports things differently to Nautilus. The Analyzer reports sda5 (actually it calls it 'disk') as having 94.3% usage (which, btw, I think is still wrong!) but Nautilus ***still*** says Free Space: 0 bytes!

Many thanks for your reply. It is very much appreciated.

---

### Post by startling on 2007-07-30
> **bodhi.zazen said:**
> Startling : I merged your three threads.

Please do not start multiple threads on the same subject:

1. It leads to a duplication of effort from those trying to help.


I'm sorry, I'm new here. I didn't mean to cause any problems. I thought by posting things in a different way I might make it clearer.


> Also, please do not bump your own threads.


I'm sorry, do you mean answer my own posts? The only reason I did that is because I kept remembering things that I thought would be helpful.

>  1. We are all volunteers here ... 


And I'm very grateful to you all; I've expressed my thanks throughout.  If it weren't for the kind people here I'd be forced to use Vista - something I'm trying to avoid!


>  2. We have an unanswered team (to help with more difficult problems), but they can not detect you need assistance if you keep bumping your thread ...

My advice to you is that you need to delete files. You need to find them.

Search you home directory, search your trash. Use Nautilus and show hidden files. Use du ...

Thank you for the advice.

However many files I keep deleting, the problem remains the same: Nautilus reckons there's 0 bytes of free space. As I posted above, Disk Usage Analyzer sees ***some*** free space.

Is this something to do with the original warning: **Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time**?

Thanks again.

---

### Post by Maxtorm on 2007-07-30
> **startling said:**
> Is this something to do with the original warning: **Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time**?
I don't think so.  In fact, if you had gksu'd instead of sudo'd nautilus, I expect you wouldn't have even seen these errors.

You indicated you did the fsck.  Did you do this from the live CD as suggested?  If so, did it report anything wrong?  Also, I have always used e2fsck, but it may be that fsck just aliases the correct command based on the filesystem type.

---

### Post by startling on 2007-07-30
> **Maxtorm said:**
> I don't think so.  In fact, if you had gksu'd instead of sudo'd nautilus, I expect you wouldn't have even seen these errors.

You indicated you did the fsck.  Did you do this from the live CD as suggested?  If so, did it report anything wrong?  

Thanks for the reply Maxtorm. If I don't get this fixed it is going to cause me major problems financially.

Here's the output of the fsck I did earlier, and yes, I did this from a terminal on the Ubuntu live CD:

```
/dev/sda5 has been mounted 37 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 144450/2240224 files (1.8% non-contiguous), 4399438/4474094 blocks
```

> Also, I have always used e2fsck, but it may be that fsck just aliases the correct command based on the filesystem type.

I'm afraid I don't really understand. Should I try e2fsck?

---

### Post by Maxtorm on 2007-07-30
> **startling said:**
> I'm afraid I don't really understand. Should I try e2fsck?
I've confirmed elsewhere: e2fsck and fsck do the same thing (when run on an ext2 filesystem).  So, no, don't bother running e2fsck as it will return the same result.

When you ran Disk Usage Analyzer, it should have returned a list that you could sort by size.  What is the largest file and/or folder on the disk?

---

### Post by startling on 2007-07-30
> **Maxtorm said:**
> When you ran Disk Usage Analyzer, it should have returned a list that you could sort by size.  What is the largest file and/or folder on the disk?

the largest folder is my home folder, and the largest file within that is a 7.9 gig iso image.

---

### Post by Maxtorm on 2007-07-30
Is that ISO file something you expect to be there (and need)?  That is accounting for 50% of the disk space on that device.  (Am I missing something from an earlier part of the thread?)

---

### Post by startling on 2007-07-30
> **Maxtorm said:**
> Is that ISO file something you expect to be there (and need)?  That is accounting for 50% of the disk space on that device.  (Am I missing something from an earlier part of the thread?)

Yes, I expect the ISO to be there. It isn't critical but I didn't want to delete it (which is why I deleted other stuff first) but I'll happily delete it if you think it would help? 

Yes, you're right about it accounting for 50% of the device, and no, I don't think you're missing anything. Before I did the backup which started all this, there was about 4 gigs' worth of free space, so when I deleted that backup file that's what I expected to get back, but even with deleting other files it has stubbornly remained at exactly 0 bytes free.

If I can't get this sorted out any other way, could I format the device and then do a fresh install of Ubuntu into that space or do you think the device might still be useless or corrupted?

Thanks again for your help.

---

### Post by Gen2ly on 2007-07-30
You might wanna look at my [old thread]("http://ubuntuforums.org/showthread.php?t=315528&highlight=dirk+space")   It's been awhile, I had almost forgotten about it.

If I remember correctly I tracked down where the files were store by this command
```
du | sort -nr
```

I can't seem to remember, its been awhile. :)

---

### Post by Maxtorm on 2007-07-30
> **startling said:**
> Yes, you're right about it accounting for 50% of the device, and no, I don't think you're missing anything. Before I did the backup which started all this, there was about 4 gigs' worth of free space, so when I deleted that backup file that's what I expected to get back, but even with deleting other files it has stubbornly remained at exactly 0 bytes free.
There's no question - this all seems totally bizarre.  OK, so the Disk Space Analyzer indicated that the ISO was your biggest file, so what did it say accounted for the next largest file/files/folders? The previous poster's suggestion for **du** will work too, but be sure to execute while in the root / folder of that drive and use sudo to ensure that permissions aren't hampering your ability to read files.
> If I can't get this sorted out any other way, could I format the device and then do a fresh install of Ubuntu into that space or do you think the device might still be useless or corrupted?If you're willing to do the format, I think it will solve your problem.  I don't think the device is in any state of failure, but that is a bit of an assumption on my part.  I think if it were failing that fsck would have indicated an issue.

---

### Post by startling on 2007-07-31
> **Maxtorm said:**
> There's no question - this all seems totally bizarre. 

Absolutely! And it's getting more weird.

From the Ubuntu CD, I just started GParted to see what it thinks. It states that there are just  316 MB free on /dev/sda5. Hmmm, it should be 4 gigs, but never mind. So I closed GParted and then deleted 42MB worth of files. I started GParted again, and it now reports 359MB. So Gparted can see *something.*

Nautilus, of course, still has its fingers in its ears, going "la-la-la I can't hear you..." It still reports 0 bytes free. Is this a Nautilus problem?

I really do need to sort this out one way or another. I cannot afford another day not working; I will lose customers.

Can you advise me on how I should format the device and re-install Ubuntu?

---

### Post by startling on 2007-07-31
> **Dirk.R.Gently said:**
> You might wanna look at my [old thread]("http://ubuntuforums.org/showthread.php?t=315528&highlight=dirk+space")   It's been awhile, I had almost forgotten about it.

If I remember correctly I tracked down where the files were store by this command
```
du | sort -nr
```

I can't seem to remember, its been awhile. :)

Thanks Dirk! (You don't run a holistic detective agency, do you, perchance?) In that thread someone mentioned that ext3 needs 5% of the drive for journalling - I didn't realise that. So while I *had* deleted files, I obviously hadn't deleted enough! I deleted a lot more and Ubuntu booted again - hooray!  I lost some data I'd rather have kept but at least I'm up and running again.

I'm still missing 3 or 4 gigs' worth of space, which seems odd, but maybe that'll turn up when I do some spring cleaning.

Many thanks for your help, everyone.

---

