---
title: "Ubuntu partition full by mistake - Now I cannot sign in."
date: 2007-12-04
forum: General Help
---

### Post by dixelpixel on 2007-12-04
I'll write the error message first:

" GDM could not write to your authorisation file. This could mean that you are out of disk space of that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

OK, here's the mistake I made: While fiddling around with my new Ipod and the stuff I had on my Lacie USB drive I managed mistakenly to fill the root on my Ubuntu partition with stuff, probably to 99 or 100%. The PC jammed and upon restart I got the message above. I am now writing to the forum from my Windows XP partition. 

I have read on previous threads on the forum that I can possibly increase the partition size of my Ubuntu partition with the Live CD. However, I imagine this would risk  damaging my Windows partition in the process andI would loose the data on both partitions. Can anyone suggest a way out? 

All help is highly appreciated

..dxpx..

---

### Post by forestpixie on 2007-12-04
If you start with in recovery mode you should be able to get rid of the files you've mistakenly copied.

Or if you're not needing too much room you could clear your apt cache - then you could (if it starts) clear the files from nautilus

```
apt-get clean autoclean
```

I believe you start as root in the recovery mode, if not prefix the command with sudo.

---

### Post by dixelpixel on 2007-12-06
Thanks for your reply.

I did try out your suggested command (apt -get clean autoclean) and got an error message saying "no such file or command" and suggesting I needed to install something, but it did not specify what.

Any suggestions? Would be a shame that such a basic mistake will shut me out of my Ubuntu partition.

All answers appreciated greatly.

..dixelpixel..

---

### Post by Crakie on 2007-12-06
Well, you could delete just about anything you don't need immediately. Boot in recovery mode and use the command "cd" to change directories and "rm" to delete files or directories. There might be some downloads in your home directory you can do without, for example.

Edit: please note - use the rm command carefully (read the manual: man rm) Some jokers have been posting fake solutions using it.

---

### Post by lvleph on 2007-12-06
> **dixelpixel said:**
> Thanks for your reply.

I did try out your suggested command (apt -get clean autoclean) and got an error message saying "no such file or command" and suggesting I needed to install something, but it did not specify what.

Any suggestions? Would be a shame that such a basic mistake will shut me out of my Ubuntu partition.

All answers appreciated greatly.

..dixelpixel..

There is no space between apt- and get

copy and paste

apt-get clean autoclean

---

### Post by dixelpixel on 2007-12-07
Hi again,

Thanks a bunch for the replies so far. Sorry to take up your time with my stupidity.

I think I can see where this is going: the problem I have created is a piece of cake to solve if you know your commands (are they called commands?) when you are in recovery mode, but impossible for noobs like me who cannot maneuver around without a GUI.

Between my last post and now I have tried to find a guide to how I can use my PC in recovery mode. I.e. find my files and start deleting stuff to get down to an agreeable disk space so I can sign in again.
However, to no avail. I cannot really find any site that helps me with the basics in recovery mode.

Any suggestions?

All help super appreciated,

..dxpx..

---

### Post by Crakie on 2007-12-07
Alright, I will try to guide you through it:

1) Boot in recovery mode. You will end up in a terminal as root (the 'user' who can do anything to your system)
2) Type: "cd /home/<your normal username>" without the ". You are now in your home directory
3) Type: "ls". You will get a list of all files and directories that are in your home directory.
4) If there are any files in there of significant size (say, an mp3 or a movie file) but not something you really want to keep, type: "rm <filename>". Copy the filename exactly, including the extention. Rinse and repeat to free up more space.
5) If there are not any files in your home directory you want to delete, use "cd <directory name>" to change the directory. Then use hint #3 and #4 to remove files.
6) You can also remove entire directories with "rmdir", but you might want to be careful with that.
7) When you are done, type "shutdown -r now". This will reboot your system and hopefully you can boot normally.

Note that I am just guessing here that you should go to /home/<your normal username>. This is where the user's data is usually stored, so it is an educated guess. If you are not sure what the files is or does, do not delete it. You are looking for movies and audio files, which have extensions such as .avi, .mpg, .mp3 etc. These are not critical for your system and safe to delete, unless you do not have a backup (and you really want to keep them).

---

### Post by gpilkay on 2007-12-07
Another thing that sometimes works is to take the Live-CD itself, boot up with that, and then use it to delete the excess files.

---

### Post by darck on 2007-12-07
I've got same error once. Shouldn't it being consider as Ubuntu bug? Why does it allow making hdd full?

To log in I had to change access permission to /tmp folder

---

