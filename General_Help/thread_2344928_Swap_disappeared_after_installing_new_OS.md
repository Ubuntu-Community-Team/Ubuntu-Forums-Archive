---
title: "Swap disappeared after installing new OS"
date: 2016-11-29
forum: General Help
---

### Post by chris-cj-perry on 2016-11-29
Hi all, I am pretty much new to Linux.

I recently set up a new system with a separate /boot and /swap partition, and installed Ubuntu 16.04 on a logical partition. Things were running fine until I installed Kali on a second logical partition. When I booted back into Ubuntu the system would freeze under heavy memory load. I suspected this was a problem with swap as I could hear the hard disk while it was frozen. I checked the UUID of my swap partition, and sure enough Kali had changed it despite me selecting Do Not Format during the graphical installation. I changed the UUID in fstab to the new UUID and rebooted Ubuntu, but it still not recognising the swap partition.

sudo swapon -a

returns:


swapon: stat of /dev/mapper/cryptswap1 failed: No such file or directory

It also is not recognised in the gnome system monitor.

How should I proceed?

Thanks for any help!

EDIT: I mounted the swap using 
sudo swapon -U UUID

The swap became visible and seems to work, but this does not survive reboot.

I suspect the problem might be in my fstab, so I will post the swap line here.

UUID=********************** none            swap    sw              0       0

I have rechecked the UUID, def correct.

---

### Post by #&amp;thj^% on 2016-11-29
Are you by chance using a encrypted swap && F/S?
EDIT: Yes I see that you are now...have a look here:
[http://askubuntu.com/questions/462775/swap-not-working-on-clean-14-04-install-using-encrypted-home](http://askubuntu.com/questions/462775/swap-not-working-on-clean-14-04-install-using-encrypted-home)
There is a bug that overwrites the UUID for the partition as soon as data is written to it. Therefore, you cannot use the UUID to reference the partition to use for encrypted swap.

---

### Post by chris-cj-perry on 2016-11-29
I don't think my swap is encrypted.
If I couldn't use the UUID to refer to it, then why does it mount when I use:
[COLOR=#000000]sudo swapon -U UUID

What makes you think the swap is encrypted if I may ask?[/COLOR]

---

### Post by #&amp;thj^% on 2016-11-29
> **chris-cj-perry said:**
> I don't think my swap is encrypted.
If I couldn't use the UUID to refer to it, then why does it mount when I use:
[COLOR=#000000]sudo swapon -U UUID

What makes you think the swap is encrypted if I may ask?[/COLOR]

About the swap, enter this in a terminal

```
sudo blkid | grep swap

```
and should see an output similar to

```
/dev/mapper/cryptswap1: UUID="95f3d64d-6c46-411f-92f7-867e92991fd0" TYPE="swap" 
```
Then you will know for sure if you are using a encrypted swap
It will still mount using  UUID but won't survive a reboot.
Regards

---

### Post by chris-cj-perry on 2016-11-30
Which part of that output would tell me whether the swap was encrypted? 
Output was the same but at my partition location not cryptswap1. There is no reason the swap partition would be encrypted, unless Kali install did it without asking.

---

### Post by #&amp;thj^% on 2016-11-30
> **chris-cj-perry said:**
> Which part of that output would tell me whether the swap was encrypted? 
Output was the same but at my partition location not cryptswap1. There is no reason the swap partition would be encrypted, unless Kali install did it without asking.

This part "[COLOR=#000080]cryptswap1[/COLOR]"
And from your first post:
> **your first post** "sudo swapon -a"

returns:swapon: stat of **/dev/mapper/[COLOR=#0000cd]cryptswap1[/COLOR] failed**: No such file or directory
There is always a reason that swap gets encrypted...weather the user meant to...or even lack of experience.   
This is usually done (encrypted) on the install you are given the choice at that stage of the install. And again maybe you were not aware of that.
Anyway the link I provided in first my post should help you sort this out...read very carefully...  the reply by  Redsandro it will begin with Bold Text "**Known Bug**"

---

### Post by chris-cj-perry on 2016-12-01
> **1fallen said:**
> This part "[COLOR=#000080]cryptswap1[/COLOR]"
And from your first post:

There is always a reason that swap gets encrypted...weather the user meant to...or even lack of experience.   
This is usually done (encrypted) on the install you are given the choice at that stage of the install. And again maybe you were not aware of that.
Anyway the link I provided in first my post should help you sort this out...read very carefully...  the reply by  Redsandro it will begin with Bold Text "**Known Bug**"

I created the swap partition using Gparted. It is not encrypted. 
 Input 
sudo blkid | grep swapdoes not return 'cryptswap', just the UUID.

The input 
sudo swapon -a 
returns like I said in my first post. 
I tested this on another system with a non-encrypted swap and it returned the same message.

---

### Post by #&amp;thj^% on 2016-12-01
Well that is new information here: "_I created the swap partition using Gparted_"
Lets see how it listed as in "/etc/fstab"
Post back the results of ths from the terminal: (just to be sure you can highlight from terminal with your mouse and right click and choose copy to paste back here.) using code tags.
```
cat /etc/fstab
``` 
This will give us something more concrete to work with here.
And I assume it shows (the swap) when booting to Kali?
And just some sound advice here if your home is encrypted back up's  always is recommended becomes vital...for repairs will not typically work on encrypted partitions.

---

