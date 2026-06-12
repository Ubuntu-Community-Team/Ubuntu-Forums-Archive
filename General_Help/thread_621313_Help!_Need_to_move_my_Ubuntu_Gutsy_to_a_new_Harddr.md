---
title: "Help! Need to move my Ubuntu Gutsy to a new Harddrive..."
date: 2007-11-23
forum: General Help
---

### Post by jonray74 on 2007-11-23
Can anyone please help me or somehow post a Guideline on how to move my Ubuntu Gutsy installation to a larger HardDrive? 

I am running out of space for my current partition and I just bought a new Harddrive to put my current installation into but couldn't find a guide on how to do it. 

I tried using Gparted and PartImage but couldn't seem to unmount my root directory. What am I missing? Shouldn't this be an easy procedure? Please help!!! :(

I would appreciate it very much!

thanks

---

### Post by LaRoza on 2007-11-23
Could you just use the new hard drive for storage? It will be simpler than try to move Ubuntu.

---

### Post by mellowd on 2007-11-23
You could move it but as LaRoza said it would be easier to just add this one. Stick it in and mount it to a new folder. Job done.

---

### Post by jonray74 on 2007-11-23
thanks, for the reply. I know I can leave the new HardDrive as a storage, but I do want to be able to move my Installation to the new  harddrive. So Isn't there a way to make the transition?

Isn't there any guide on how to do this kind of procedure? I don't want to keep adding harddrives in my box... can someone there help me please..

thanks

---

### Post by mellowd on 2007-11-23
> **jonray74 said:**
> thanks, for the reply. I know I can leave the new HardDrive as a storage, but I do want to be able to move my Installation to the new  harddrive. So Isn't there a way to make the transition?

Tar your whole system, install linux on the new hard drive with the same partition sizes and then extract your backed up tar file over it. reboot and you'll be back.

---

### Post by jonray74 on 2007-11-23
can you post the guide on how to do it please...or possibly the link?

thanks

---

### Post by mellowd on 2007-11-23
I don't have a guide, but if you wanted to tar everything you do this:
```

tar -zcvf system.tar.gz --exclude=system.tar.gz /
```

backup that file externally.

Once you have reinstalled on the new hard drive (remember to ensure your partition size matches for this)

move your backup file back to the root of your new installation and type this:

```
tar -zxvf system.tar.gz /
```

---

### Post by jonray74 on 2007-11-23
hi

I noticed you have "-zcvf" and "-zxvf", what's the difference?

I tried running it but i've got some warning messages, are those normal?

thanks

---

### Post by didds on 2007-11-23
Try This

[http://linuxbasics.org/tutorials/advanced/various/mypartitionisfulldoineedtoreinstall](http://linuxbasics.org/tutorials/advanced/various/mypartitionisfulldoineedtoreinstall)


diddy

---

### Post by jonray74 on 2007-11-23
thanks diddy for the link, but i think that's a little too complicated to follow. Is there a simple way than doing this?

I tried running the TAR but i got so many errors running that command.

---

### Post by mellowd on 2007-11-24
> **jonray74 said:**
> hi

I noticed you have "-zcvf" and "-zxvf", what's the difference?

I tried running it but i've got some warning messages, are those normal?

thanks


z - compression
c - create
x - extract
v - verbose
f - file 

Hope that answers :)

---

### Post by jonray74 on 2007-11-25
I tried running it but i've got some warning messages, are those normal?

:(

---

### Post by mellowd on 2007-11-26
> **jonray74 said:**
> I tried running it but i've got some warning messages, are those normal?

:(

What does the warning message say?

---

### Post by mr_firefox on 2007-12-03
I'm in the same situation. I have two partitions on my hard disk, / and /home

I'm planning to buy a motherboard bundle to rejuvenate performance (I'm currently using an AMD Athlon 2200+ system I built back in 2002/2003)

But the new motherboard will come with a faster SATA drive, so I'd like to shift /  and /home in there and perhaps keep the old hard drive for backing up purposes (It is 49.2 Gb)

So all I need to know is, how do I transfer this system into the new SATA drive?

Is it possible to use Ghost or a similar tool to make life easy?

I've looked through previous replies and they don't appear to achieve what I need, which appears to be the same as the original poster (I hope you don't mind me gatecrashing!)

Thank you

---

### Post by mr_firefox on 2007-12-05
:confused:

---

### Post by mr_firefox on 2007-12-05
*bump*

---

### Post by ntu on 2007-12-05
I use Clonemaxx to clone one hdd to another. It is free. You can download it from here:
[http://www.pcinspector.de/Sites/clone_maxx/info.htm?Language=1](http://www.pcinspector.de/Sites/clone_maxx/info.htm?Language=1)

---

### Post by mr_firefox on 2007-12-06
Thanks!

I'll check that out.

---

