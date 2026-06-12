---
title: "A Guide to Creating a TrueCrypt 4.3a Hidden Volume"
date: 2007-12-01
forum: General Help
---

### Post by mahousaru on 2007-12-01
I couldn't find much information about creating a TC hidden volume apart from what was in the man which says to follow the example which is quoted below:

> 
Creating a hidden volume without risking data corruption:

    1) Create an outer volume: 
    truecrypt --type normal --size 100M -c volume.tc 
    2) Create a hidden volume: 
    truecrypt --type hidden --size 50M -c volume.tc 
    3) Mount the outer volume with the hidden volume protected: 
    truecrypt -P volume.tc /mnt/tc 
    4) Copy files to the outer volume: 
    cp outer_volume_file.txt /mnt/tc 
    5) Dismount the outer volume: 
    truecrypt -d volume.tc 
    6) If a warning message has been displayed in 5), start again from 1). Either a larger outer volume should be created in 1), or less data should be copied to the outer volume in 4). 


What is missing from the example is that the outer volume must be formatted as FAT so select choice 1 when TC asks what file system you wish to create during step 1.  

**But there is a bug** which some clever chap on the TC forums found out about.  If you follow the above guide you will always get a failure message when you do step 5.  It will complain that it has protected data from being over written and say that it has protected it.  For some reason it doesn't protect the data and corrupts what was being copied across.  To fix this you need to do step 1a and manually format the partition:

Step 1a)  After creating the outer volume, you must mount it, run mkfs.vfat and then dismount it.

```

truecrypt volume.tc
truecrypt -l

```

If this is the only TC volume mounted you should see something like:
/dev/mapper/truecrypt0 volume.tc
Now format it with vfat and dismount it.

```

sudo mkfs.vfat /dev/mapper/truecrypt0
truecrypt -d /dev/mapper/truecrypt0

```

With part 3, you may run into issues as it will mount it as root and we don't like root, so mount it with your user rights instead (little u)

```

truecrypt -uP volume.tc /mnt/tc

```

Now after you dismount the volume it should not fail.

You will need to format the hidden volume before you can write to it, it **does not need to be fat**.  The steps are the same as above but make sure you use your hidden volume password.

Remember unless you are updating the fake data on the outer volume you don't need to use the -uP.  Also consider disabling your history as you loose deniability when someone sees that you are mounting a protected volume.

*All credit goes to the clever chap on the TC forums for finding this bug which was driving me insane*

---

### Post by niteshifter on 2007-12-01
Hey - thanks! I've been stumbling over this exact problem for a while now!

> Also consider disabling your history 

Easy trick for this: Set the environment variable HISTCONTROL to IGNOREBOTH. Then preface any command you don't wish remembered with a space.

---

### Post by mahousaru on 2007-12-01
> **niteshifter said:**
> Hey - thanks! I've been stumbling over this exact problem for a while now!



Easy trick for this: Set the environment variable HISTCONTROL to IGNOREBOTH. Then preface any command you don't wish remembered with a space.

That is a great tip thank you!

---

