---
title: "Help with move to separate /home partition"
date: 2006-11-14
forum: General Help
---

### Post by norcalnewb on 2006-11-14
I  followed thw psychocats.net tutorial on creating a separate /home partition.  Everything seemed to go well until I started copying data from the old /home to the new partition.  Many of my wife's files were not copied from her home folder as I got a message that access was denied.  I was using sudo during the cpio command, but still go this message.  Is there a way around this?

---

### Post by pay on 2006-11-15
sudo should be able to copy them. What command did you use? Try ```
sudo cp -r /path/to/WIFE'S_USER_NAME /home/WIFE'S_USER-NAME
```

---

### Post by koenn on 2006-11-15
similar problem + help here : [http://www.ubuntuforums.org/showthread.php?t=299985](http://www.ubuntuforums.org/showthread.php?t=299985)

---

### Post by Ramses de Norre on 2006-11-15
> **pay said:**
> sudo should be able to copy them. What command did you use? Try ```
sudo cp -r /path/to/WIFE'S_USER_NAME /home/WIFE'S_USER-NAME
```

Don't use this command, without the -a option cp wont copy links over correctly, so you want to either use the -ar option or use the find command from psychocats.

Can you try to do it after a sudo -s? So that you're permanent root?
And you are copying from ext3 to ext3, right?

---

### Post by norcalnewb on 2006-11-15
I'll give the sudo -s option a try.  I am copying from ext3 to ext3.  I just reformatted my other hard drive, which still had all my winxp stuff on it, to ext3 to make this the /home partition.

All of my files, both hidden and normal copy fine, it is only my wife's files.  I would like to avoid changing the permissions on her files if I could.

---

### Post by Ramses de Norre on 2006-11-15
Permissions will remain; only ownership could change after a copy as root, but that's solved with a simple ```
sudo chown -R wifes_username:wifes_username /home/wifes_username
```

---

### Post by norcalnewb on 2006-11-17
OK, I think I got the move completed.  I have just one bug that I can tell now.  I get the following error when using evolution:

Error while Storing folder 'Inbox'.
Summary and folder mismatch, even after a sync

I am not sure how to fix this one.  Thanks for all of your help so far.

---

### Post by petersjm on 2007-01-06
> **norcalnewb said:**
> I  followed thw psychocats.net tutorial on creating a separate /home partition.  Everything seemed to go well until I started copying data from the old /home to the new partition.  Many of my wife's files were not copied from her home folder as I got a message that access was denied.  I was using sudo during the cpio command, but still go this message.  Is there a way around this?

In case it's of any help to anyone, I'm in the middle of creating a new /home partition and ran into the same permission-denied problem as described above. But when I looked at the command I had entered, it turned out my keyboard is different on LiveCD than local install - I guess GB to US... so the | key was in a different place and I had actually pressed > instead. That's why it didn't work... When I corrected it, it all went according to plan.

---

### Post by markd on 2007-01-11
I had a similar permissions problem following the psychocats howto at the same point.  I thought that the 'find' might need a sudo as well as the 'cpio' so that it could access all files in the old home dir. That did the trick for me.

---

