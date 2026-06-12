---
title: "[SOLVED] Setting up a Network Hard Drive"
date: 2007-09-26
forum: General Help
---

### Post by Nehvrook on 2007-09-26
So I just bought a network hard drive to replace my old external which is bust. It can be connected to the network through the router or the PC as a normal external by USB. This is the first time I've used one so I'm a bit lost

I installed the software on Windows and managed to see the files eventually.
But I have no idea how to see it on Ubuntu.

So I'd like to know if I need to install anything and what to do to be able to access this drive in Ubuntu.

I've looked around and can find very little help on the topic. I've seen a program called Samba mentioned but I'm not sure if that's what I need.

Thanks for any help :)

---

### Post by reckless2k2 on 2007-09-26
so do you have it installed on the network or plugged into your pc as an external drive?

you usually have to go to the admin webpage if it's on the network. make sure your workgroup is all the same and you can usually navigate to it right in ubuntu using the network connections in the middle menu. places?

you usually have to go through a process setup on the gui web admin page. then you'll know the IP address, device name, share...etc..users/passwd.

---

### Post by Nehvrook on 2007-09-26
Ah sorry. I tried it plugged into the PC to make sure it works (Which it does) but now it's in the network.

By admin webpage do you mean my routers menu, or one for the hard drive? I know the hard drive has one but I don't know it's IP address. The application on Windows launched it for me (Hate how windows does stuff without telling you how it did it)

I'll have a look through the manual see if I can see an IP address.

---

### Post by bigken on 2007-09-26
look in your router for attached devices for the ip address

just a thought cant you give it a static ip address the the windows application

---

### Post by Nehvrook on 2007-09-26
Okay. Can't find any sort of attached devices in my router settings. But I'm pretty sure I can give it a static IP address in Windows. Give me a few minutes to re-boot and try.

---

### Post by Nehvrook on 2007-09-26
Right. I've given it a static IP address and I can now log into it's config utility in Ubuntu.

So I've went to Places > Connect to a network

I chose Windows Share and put in that IP address and I can now access the hard drive in Linux perfectly :D

That was just a guess but it worked. Is it the correct way to access the drive? At least I have it working now correct or not. Thank you for your help, though I should probably have thought on it a bit more and I could have solved it without bothering you :P

---

### Post by bigken on 2007-09-26
pleased your sorted :)

---

### Post by notwen on 2007-09-26
Glad you got it up and running.  Good to know these are easily setup in Ubuntu, I've been eying a 1TB one for a while now.  Might hafta spoil myself and pick one up towards the end of the year.  =]

---

### Post by reckless2k2 on 2007-09-26
you can fstab mount this on ubuntu permanently if you like which will make it perfect for video and music. i do this already with my NAS. what you have is termed as a NAS (network attached storage). when you get around to needing that fstab functionality, just call on us if you can't figure it out.

oh and mark this baby as SOLVED......i'm getting brownie points!!!!

---

### Post by chrome307 on 2007-09-26
How is your NAS drive formatted??

Will you need **NTFS-G** to be able to read/write to this device??

Also can you let us know which model you have, this way if anyone reads the thread they know what to purchase :)

Thanks

---

### Post by Nehvrook on 2007-09-28
Sorry. The drive came formated in FAT32, so there was no need for extra drivers to use it.

And it's a Freecom, but I can't see any sort of model number. The box just says

"Freecom Network Drive 250GB external network hard drive/3.5"/LAN/USB2.0"

and the bar code says "Model Code: SSLABC"

other than that there doesn't seem to be a model.

Marking this as solved now

---

