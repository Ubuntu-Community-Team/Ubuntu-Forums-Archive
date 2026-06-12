---
title: "Swap"
date: 2014-06-16
forum: General Help
---

### Post by benalexb on 2014-06-16
Hi there,

This weekend I decided to try out linux and installed Xubuntu. Please excuse my ignorance when it comes to Linux, as I'm still learning. My first attempt failed, as I tried installing it without swap (didn't think I was gonna need it, since there's 32 gigs of ram). The second attempt was a success, but I noticed the OS created a third partition on the SSD as swap, and gave it 32 gigs of space (which makes sense, as I believe it will mirror the amount of ram on the system, am I right?). So I was left with some questions:

(1) Is swap mandatory? As I don't think I'll be running out of RAM anytime soon.
(2) If swap is indeed mandatory, then does it necessarily need to mirror the exact amount of RAM on the system, or can I give it less than 32 gigs?
(3) Does the swap partition need to be on the same hard drive? I have a second hd, and I wonder if I could set the swap there, instead of using the SSD where I have installed the OS. The ssd is only 120gb, and I lose 32gb just in swap...

At any rate, I'm loving Xubuntu so far! Installing it was fast and hassle-free; setting up my dev environment was a breeze with apt-get. Everything is working, AND, super fast (maybe because of the ssd?).

In advance, thank you for the help. I do appreciate it.

Sincerely,
-Ben

---

### Post by vanadium on 2014-06-16
> **benalexb said:**
> Hi there,
(1) Is swap mandatory? As I don't think I'll be running out of RAM anytime soon.

It is backup memory. If there is not enough physical memory, the system can start to use the much slower swap memory. In addition, SWAP is used for hibernation.

If you use hibernation, you need the swap. The need to have swap to safely run your system is less. With 32 MB of RAM you will hardly if ever need swap.

> 
(2) If swap is indeed mandatory, then does it necessarily need to mirror the exact amount of RAM on the system, or can I give it less than 32 gigs?

You can give it less, unless you want to be able to hibernate the system.
> 
(3) Does the swap partition need to be on the same hard drive? I have a second hd, and I wonder if I could set the swap there, instead of using the SSD where I have installed the OS. The ssd is only 120gb, and I lose 32gb just in swap...

It can be anywhere. In old systems where swap was regularly used, it would be put on the fastest disk. In your case, where you hardly need it while running the system, it is indeed a waste to have it on your fast SSD drive: you better move it to another drive.

---

### Post by LastDino on 2014-06-16
If you're not going to hibernate (which requires exact amount of SWAP as your RAM), you can leave 2GB for curtsy of it.  That should answer 2 of your questions.

No, it doesn't need to be on same drive. IMO SSD has too little of space to use it as SWAP, which is just going to seat there.

---

### Post by grahammechanical on 2014-06-16
Swap is not mandatory but to keep installing simple for the user the developers make certain assumptions and needing swap is one of the assumptions. Many people are switching to Linux from Windows XP and those machines will need swap.
 
The alternative to the developers making these assumptions would be a long list of choices that the would be user has to make. And that puts people off, especially if they are completely new to Linux and installing Ubuntu and its flavours and do not understand what the choices represent.

Regards.

---

### Post by benalexb on 2014-06-16
Thanks everyone! With the information you provided me, I believe I know how to proceed from here.

Gratefully,
-Ben

---

### Post by ken0069 on 2014-06-16
Since my question is similar to the OP I'm going to add this on.  If it needs to be in it's own thread then please separate it off and make another.

I too have gone to an SSD and Ubuntu 14.04 only I used a 32GB SSD drive just for the OS.  The computer in question is a multi boot and all data saved from Ubuntu (documets, pics, downloads, etc) are stored on a 1TB storage drive formatted NTFS so that data is alway available whether Ubuntu will boot or not.  The system has a 3.16 Xeon Quad and 8GB DDR2 PC 6400 memory and I'm wanting to free up that 8gb swap space on the SSD for other use.  

So can someone tell me how to delete that swap partition and make it so I can use the entire 32GB?  There's no need to have an 8GB partition sitting there doing nothing while the rest of the drive is being worn out from daily use.  

Thanks

Ken

---

### Post by LastDino on 2014-06-16
Simplest way to do that would be to delete the fstab entry of swap partition and then boot into Ubuntu LiveCD/USB and delete/edit that partition to whatever you want.

First look up your SWAP UUID
Command
```
sudo blkid
```

It should give you output like this
```

/dev/sda1: UUID="59bc15ce-9ec0-4760-9ebf-9752388e8837" TYPE="ext4" 
/dev/sda3: UUID="f53e9947-65fa-47e3-a805-42ac1c92f191" TYPE="ext4" 
/dev/sda4: UUID="079cccfe-58c1-4a11-9f2d-f68add0ba943" TYPE="ext4" 
/dev/sda5: UUID="27ccab72-8110-46ad-aba6-6fdcc984df61" TYPE="ext4" 
/dev/sda6: LABEL="Storage" UUID="378b48ff-56dc-4650-b7a6-5c2202dfd7ee" TYPE="ext4" 
**/dev/sda7: UUID="209d2e66-bf09-460f-9ee4-ef6f81053fa8" TYPE="swap" **
/dev/sda8: LABEL="L2" UUID="533f9425-b342-4099-9d63-1723cc9c5f1e" TYPE="ext4" 
/dev/sda9: UUID="ad645074-a963-46bf-852a-b4e4ba3ac86c" TYPE="ext4" 
/dev/sda10: UUID="cf4ca9f3-2315-4bb5-a49b-8e3367991b8d" TYPE="ext4

```

As you can see, I've my SWAP on /dev/sda7

Then turn off your SWAP
```
swapoff /dev/sda7
```

Then open fstab to edit it.
```
gksu leafpad /etc/fstab
```
You can use whatever text editor you've installed on system instead of leafpad, example: Mousepad. Or even ''nano'' to edit it in terminal itself, but that will require you to know few things more.

Remove the line which looks like this
```
[COLOR=#333333][FONT=UbuntuMono]# /dev/sda7
[/FONT][/COLOR] UUID="209d2e66-bf09-460f-9ee4-ef6f81053fa8"none  swap  sw  0  0
```

If you're not able to edit this while booted in, use LiveCD/USB to do so. 

Now you're free to do whatever you want with that extra 8GB.

And yeah, you need to make new thread for your issue even if there is someone else with the same :3

---

### Post by benalexb on 2014-06-16
Ken0069, thanks for your questions, and LastDino, thanks for your response. I'll most likely need to do the same thing. I wonder if I'll need to do a clean install though, after fixing the partitions.

---

### Post by LastDino on 2014-06-16
Gparted does allow  you to extend/move/re-size like operations on existing partitions if you don't want to keep that 32GB as separate partition. However, you need to do that when disk is *not mounted*, means; you need to use Ubuntu LiveDVD/USB and use Gparted from there. Basically adding one more step to the above post of mine. 

I would backup everything important just in case though. 

If I was in your place, I would also read up on Linux file system, partitions and gparted before attempting this. Its not a big read, it will save you of lot of frustration and serve you well in long run.

---

### Post by benalexb on 2014-06-16
Thank you again LastDino!

---

### Post by ken0069 on 2014-06-17
@LastDino, it's done and working fine so thanks for your help!!!  I had done this several years back but had forgotten what was involved or where I got the info to complete it.  

One word of caution though.  Instead of deleting that swap UUID line I use the double hash tag (##) in front of that line so it's not read.  That way if something horks up and I need that line back in, all I have to do is remove the double hash.  

Ok so now I'll start another thread soon to try to find out why NTFS Config won't let me auto mount my Windowz drives.  ;)

Ken

---

### Post by LastDino on 2014-06-17
> **ken0069 said:**
> @LastDino, it's done and working fine so thanks for your help!!!  I had done this several years back but had forgotten what was involved or where I got the info to complete it.  

One word of caution though.  Instead of deleting that swap UUID line I use the double hash tag (##) in front of that line so it's not read.  That way if something horks up and I need that line back in, all I have to do is remove the double hash.  

Ok so now I'll start another thread soon to try to find out why NTFS Config won't let me auto mount my Windowz drives.  ;)

Ken

I'm glad to hear things are working fine for you. Also, thank you for sharing that info, that is much better way to work with considering how easy it is to go back if things end up being messy.

---

