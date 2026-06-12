---
title: "Migration of Truecrypt volume from Windows 7 to Ubuntu"
date: 2017-01-15
forum: General Help
---

### Post by alku1 on 2017-01-15
I finally got my first installation of Linux (Ubuntu 16.04) up and running! :-)
However I was quite shocked when I recognised that my encrypted volume is not recognised!

Previous system:
Windows 7 64 
3Ware/LSI 9650SE RAID 5 Array
Truecrypt 7.1a

New system:
Ubuntu 16.04
same hardware


I used a password & keyfile. The keyfile was migrated from being stored on the NTFS Windows partition towards a NTFS USB stick.
The Controller was setup and Im able to login the web interface. RAID array status is OK and I can see the volume in the device manager. However, after selecting auto-mount and putting in password and keyfile Im getting just an error that either pw or keyfile is wrong. :(:(:(

The only thing I can think of is that the keyfile might have been slightly altered due to the different format of the drive?
Any other ideas / hints which would help out?

---

### Post by Kestreln8144 on 2017-01-15
Hello alku1. I'm not an expert, but I've also used Truecrypt on Ubuntu, so maybe I can help.

Are you trying to mount an encrypted partition, or a file?

Also, are you using Truecrypt, or Veracrypt? (If you're using Veracrypt, it requires a special switch to mount Truecrypt-created volumes.)

Have you tried manually selecting the correct volume and mounting it?

---

### Post by alku1 on 2017-01-15
Thanks for your reply!

I have neither a partition nor a file. I simply have a huge block of unallocated space. somewhere in there is a truecrypt encrypted ntfs partition spanning the whole drive. 
So isually I just went to auto mount, select a drive letter, keyfile and put in my pw and checked the box for show your pw to doublecheck that its right. I tried that with truecrypt and veracrypt (checking the extra truecrypt volume switch) but both dont work. I even manually selected the drive with the unallocated space but that didnt help either. 

The only thing which might be an option is to get another harddrive and install win7 again to mount the encrupted partition there, copy everything to another disk and freshly set up a new encrypted partition under ubuntu and copy back the data from the separate drive. 
Of course thats a pain in the neck since i need to buy a new hd and move 9tb of data...

so any other solution would be really appreciated!!

---

### Post by Kestreln8144 on 2017-01-15
So the entire drive is encrypted, not merely a/the partition?

When I first encrypted my own external storage drives, I chose to encrypt the entire drive instead of creating a partition and encrypting the partition. Truecrypt on Ubuntu had trouble using this drive for reasons I don't understand, so I switched to an encrypted partition instead. It's what I would recommend to people encrypting drives with Truecrypt/Veracrypt.

For the safety of your encrypted data, I would suggest doing the Windows install and seeing if the drive works from there. It might be possible to access the drive from a VirtualBox Windows VM; I've never done that so I can't be sure.

I know it's a pain, but if I were in your shoes, it's the best thing I could think to do, unless someone else here has a better idea. I'm sorry that I don't have better knowledge about these issues.

---

### Post by alku1 on 2017-01-16
I just ordered a new drive so i will test it this afternoon with a reinstall of Windows. 
Thanks for the hint that partitions are better than volumes under ubuntu. Do you have any more details on the matter?

So far I preferred to use plain volumes for privacy/security reasons. If you cant see the drive, you dont miss/look for it ;-)

EDIT: After a reinstallation of Windows aôn teh new drive I was able to mount my Truecrypt volume as usual. I copied all data and I am in the middle of the process of creating a new Veracrypt encrypted device. However, this didnt work from the beginning because I received an error message. With the help of google and this Forum I found out that there is a certain package missing for making Ubuntu work properly with Veracrypt and Truecrypt:

[B]sudo apt-get install dmsetup
[/B]
So my guess is, that with dmsetup installed, my inital problem would have been solved, too. Of course at this stage I cant test it anymore since, however, that info might help some other folks out there who have issues with mounting their old containers on 16.04!

---

### Post by Kestreln8144 on 2017-01-19
I'm glad to hear you can still access your drive. Seems strange that dmsetup wasn't installed by default, since it is for me. (Although I have Xubuntu, so maybe vanilla Ubuntu is different?) Truecrypt/Veracrypt does use device mapping to mount volumes (for example, a mounted volume of mine is listed as a drive under /dev/mapper/veracrypt1), but this is only after the volume is found and mounted, not before. AFAIK your drive should've been listed like any other drive, for example as /dev/sdb or /dev/sdh, so that wouldn't explain to me why it couldn't be found.

In any case thank you for sharing that, it will definitely help people. If you can successfully mount the new volume on Ubuntu, be sure to let us know it works and mark the thread as "Solved". (Under the "Thread Tools" menu at the top right.)

---

### Post by alku1 on 2017-01-20
short clarification: the drive itself was found before as sdX or something. however, it couldnt be mounted by either veracrupt or truecrypt. but the system recognised it correctly as a drive without partitions :-)

---

