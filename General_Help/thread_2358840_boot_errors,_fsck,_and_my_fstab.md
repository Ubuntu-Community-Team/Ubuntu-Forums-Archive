---
title: "boot errors, fsck, and my fstab"
date: 2017-04-17
forum: General Help
---

### Post by wilsonaaronm08 on 2017-04-17
Hey Y'all,

I have an annoying boot error undoubtedly caused by me, although I'm not sure what I did. Right before login I see a "error 2 while executing fsck.ext4 for /dev/sda1" error. It also takes forever to boot if I have a thumb drive, external drive, or smart phone (P.I.T.A.) plugged into usb when I boot. I think this is connected to my fstab file but I'm not sure.

Here's output for sudo blkid: ```
/dev/sda1: LABEL="/" UUID="b9000583-5bd2-478d-b26c-401651f9dfe8" TYPE="ext4" PTTYPE="dos" PARTUUID="00054445-01"
/dev/sda2: UUID="deee7164-95cd-444d-8f87-f70c63bdf14e" TYPE="swap" PARTUUID="00054445-02"
/dev/sda5: UUID="c28a24d5-fcb3-4273-a895-9f5c6811746b" TYPE="ext4" PARTUUID="00054445-05"
```

Here's what /etc/fstab looks like: ```

UID=b9000583-5bd2-478d-b26c-401651f9dfe8            /             ext4      defaults              1      1


#UUID=eee7164-95cd-444d-8f87-f70c63bdf14e            swap          swap      defaults              0      0
```

Any help would be appreciated!

---

### Post by Dennis N on 2017-04-17
You have two potential problems that I see in the fstab.

In first line, UID should be UUID,
and
You have the line for the swap partition commented out. Remove the # at start.

---

### Post by wilsonaaronm08 on 2017-04-17
Wow, this is why I needed so many proof readers while I was in school.

That seemed to have made the error go away but the boot time is actually slower now (sticks around at the splash screen forever). I'll try booting with a thumb drive in and see what happens.

---

### Post by wilsonaaronm08 on 2017-04-17
Ended up deleting swap from gparted and getting rid of it in fstab. Much faster now! Not really sure I needed swap anyways. Wish I would have figured this out a year ago!

---

### Post by Bucky Ball on 2017-04-18
> **wilsonaaronm08 said:**
> Ended up deleting swap from gparted and getting rid of it in fstab. Much faster now! Not really sure I needed swap anyways. Wish I would have figured this out a year ago!

If you are happy, please mark the thread as solved to help others. As for the /swap partition, whether you need one or not would depend on the amount of RAM. Did you check that the UUID you had for the /swap partition was correct? If you would have, you'd have noticed that you had the wrong UUID. That is why things were slow, not because you had a swap.

You were missing a 'd' from the beginning of your entry for /swap in fstab. This can be clearly seen in the output from blkid. Deleting the /swap then the /swap partition fixed this. Removing the faulty fstab entry is the reason you fixed this, not removing swap. Removing the fstab entry (or better still fixing it) would have fixed this problem. ;)

You killed a mosquito with an elephant gun. All you needed was a 'd' at the beginning of the UUID for your /swap entry in fstab and job done.

---

### Post by wilsonaaronm08 on 2017-04-18
Mosquitos are terrible here in Michigan. If I decided to have swap again I'll make sure to type everything correctly. Lesson learned!

---

