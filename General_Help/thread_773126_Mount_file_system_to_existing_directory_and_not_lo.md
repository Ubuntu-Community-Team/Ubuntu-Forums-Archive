---
title: "Mount file system to existing directory and not lose data in that directory"
date: 2008-04-28
forum: General Help
---

### Post by TurboRush on 2008-04-28
Hello...

Quick question... I previously had a dual boot setup where Ubuntu lived on one 320g drive and Vista lived on a separate 320gig HD (not partions, physical drives).

For obvious reasons I no longer have a use for Vista and wiped the HD clean and reformatted and temporarily mounted at a random point and did some copying, etc to make sure everything looked good.

What I would like to do is use my home directory as the mount point. However, I have quite a bit of data in my home directory. Is there a way "overlay" this without physically copying all of the data to the new drive first and then changing the mount point to my home directory?

---

### Post by Glaxed on 2008-04-28
yup, 2 options -

1. Create a new folder in your home directory and mount in there.
2. Go ahead and mount the whole HDD in your home anyway - Ubuntu manages it as a matter of permissions and is mature enough to not delete your files when you do this.

So I would;
$ sudo mount -o rw /dev/yurhddX /home && sudo chmod -R -v 777 /home/username

---

### Post by TurboRush on 2008-04-28
> **Glaxed said:**
> yup, 2 options -

1. Create a new folder in your home directory and mount in there.
2. Go ahead and mount the whole HDD in your home anyway - Ubuntu manages it as a matter of permissions and is mature enough to not delete your files when you do this.

So I would;
$ sudo mount -o rw /dev/yurhddX /home && sudo chmod -R -v 777 /home/username

Thanks for the input. I gave option #2 a shot and I think I might be missing something..

I created a directory /media/drive2 owned root:root. I then copied about 10g of data to /media/drive2 also owned root:root. I then did...

```
sudo mount /dev/sda3 /media/drive2 && sudo chmod -R -v 777 /media/drive2
```

That works fine, the drive mounts but when I then go /media/drive2 its empty.

```
sudo umount /media/drive2
```

and my files "return".. So, I was hope that I could see the 10g I copied pre-mount after I do the mount. Am I misunderstanding how this should work?

---

### Post by Glaxed on 2008-04-28
No, you aren't.
I think I'm being unhelpful, if that's helpful :).
Could you try that again, but instead of un-mounting, try to cd into /media/drive2 and do
```

$ sudo ls | more

```
I really do not know why this is happening to you. I guess I would just create a separate folder for your 10GBs, and another for your sda3... But don't give up yet, there has to be a fix.

---

### Post by TurboRush on 2008-04-29
No luck... mounted and ls -la just gives . and ..

I believe it's close. I had remeber reading that this could be done and it was basically what you said. Probably just missing something small.

---

### Post by TurboRush on 2008-05-02
Well, I did some more searching and couldn't really find anything that said you can "overlay" and have the files in the directory just appear in the FS. More references to the fact that you can mount the HD at the same point but not lose the data that is already in the directory.

So... just created a temporary mount point, copied everything from /home to the temp mount point, unmounted it and remounted it to /home. Original data stays in place behind the scenes if the drive ever fails and in the mean time I am writing to the new drive.

---

