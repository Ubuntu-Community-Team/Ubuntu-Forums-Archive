---
title: "I screwed up my filesystem permissions"
date: 2007-09-05
forum: General Help
---

### Post by tnurba on 2007-09-05
I have been messing around in ubuntu for a few months now and I really love it.

but for some reason I decieded it would be a good idea to change the file permissions on all the folders under "/"  to read and write for the "group" and "other" and i made sure to apply this to all sub folders and files.

After doing this i noticed that that was a big mistake and i was no longer able to access anything and my system is totally screwed up...so when i rebooted it goes to "cannot access tyy".

I know I screwed up by doing this...but how do I fix this....I need to put the permissions back to how they were..

Please tell me there is an easy way to do this.

---

### Post by tnurba on 2007-09-05
please is there anyway to correct this??

---

### Post by splintercellguy on 2007-09-05
Ouch, very bad idea. You've screwed the permissions for a lot of system files, backup and reinstall.

---

### Post by tnurba on 2007-09-05
oh crap...I just got my mythtv fully setup with all my pictures videos etc...it took me hours to get all of that setup...

how would i back everything up when i cant even boot into the system???

please help!!

---

### Post by merlinus on 2007-09-05
You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```

will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute the ubuntu partition from fdisk -l for sda2)

-merlin

---

### Post by tnurba on 2007-09-05
Thanks for the reply...

I did as you said and I was able to mount the filesystem...but i still cant go into folders or anything..

I dont remember exactly where all my files are for mythtv...

now what??

---

### Post by merlinus on 2007-09-05
You may be able to access folders and files running nautilus (file manager) as root:

```

gksudo nautilus

```As for location of your data, quien sabe?

You might activate Show Hidden Files in nautilus and look in /home/username.

-merlin

---

### Post by Nythain on 2007-09-05
sudo chmod -R a+rwX /media/ubuntu (not the current / but the old / you have mounted via liveCD... probably something like /media/hda1 or whatnot, you get the point) MIGHT, possibly, maybe, not to sure, help you in this endeavor... basically, that command is going to make it to where anyone and everyone can read/write all teh files contained in the old root system, and set all Directories to executable, so you can actually go into them... that way you can access everything to back it up before your re-install

---

### Post by tnurba on 2007-09-06
I was able to mount the old file system and get to all my files...i went ahead and resized the drive and made a new partition and installed ubuntu freash on that partition.

I still have the old partition under /media/sda3 and i can get to all my files.
How would i go about restoring my system back to how it was before i screwed it up??

---

### Post by merlinus on 2007-09-06
/home/username has all of your email, bookmarks, settings, preferences, etc.

Other than data, it is probably not worth the time and effort to copy over anything else.

-merlin

---

