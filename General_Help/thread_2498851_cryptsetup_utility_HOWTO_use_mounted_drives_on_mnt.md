---
title: "cryptsetup utility: HOWTO use mounted drives on /mnt"
date: 2024-07-01
forum: General Help
---

### Post by Old Jimma on 2024-07-01
Hello Ubumtu People:

I've successfully installed Ubuntu with full disk encripiton! Yaaay!!!

I want to encrypt "drives" that I've mounted at /mnt so that they are encrypted, also. Those drives are mounted at startup at:

> 
/mnt/DRIVE1
/mnt/DRIVE2


I was advised to use che cryptsetup utility and found advice at this URL: [HTML] https://www.cyberciti.biz/security/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/ [/HTML]

I have installed crypset up, and reached "STEP 2:  Configure LUKS partition" of the HOWTO.

It says: to issue the command:

> 
fdisk -l
... probably for the purposes of finding the device one wants to encrypt.

**None of my mounted drives are listed there! Is that because I mounted them at starup at /mnt ??**

Then, the HOWTO says to issue the follosing commands:

> 
cryptsetup luksFormat --type luks1 /dev/DEVICE
cryptsetup luksFormat --type luks2 /dev/DEVICE


I tried this with:

> 
cryptsetup luksFormat --type luks1 /mnt/DRIVE1
cryptsetup luksFormat --type luks2 /mnt/DRIVE2


and it did not work!

My questions are:
[LIST]
[*]what is luks1 and luks2 in those commands?
[*]should I have mounted my drives at /dev instead of /mnt?
[*]Am I heading down the right path with this?
[*]How do I get cryptsetup properly configured?
[*]
[/LIST]

THere isn't much on that web page that expains stuff in any detail to a person like me who doesn't know!


Thank you!
Old

---

### Post by TheFu on 2024-07-01
LUKS containers can have different types according to the cryptsetup manpage, 
> Device type can be plain, luks (default), luks1, luks2, loopaes or tcrypt.
If we assume that luks2 is newer than luks1, then we should always format using the latest available, lacking any specific reason to use some older version.

More from the manpage:
>               For LUKS1, only PBKDF2 is accepted (no need to use this option).   The  default  PBKDF2  for
              LUKS2 is set during compilation time and is available in cryptsetup --help output.


Reads like LUKS2 is newer and provides for new features that LUKS1 doesn't support. For example, LUKS2 supports different sector sizes, which could be helpful sometimes. There are many other options that only LUKS2 supports.

There are many, many, caveats that are documented in the manpage, so if you really need to avoid problems, you'll need to read it. Nobody else will care about your security or data in the same way that you do.

---

### Post by currentshaft on 2024-07-01
sudo fdisk -l
sudo cryptsetup luksFormat <path to /dev/disk>
sudo cryptsetup luksOpen <path to /dev/disk> <unique label>

Note that luksFormat is a destructive operation which will erase whatever is on the destination device, so pick carefully.

You'll need to make a filesystem on the LUKS-formatted partition, using "sudo mkfs.ext4" for example. Then you can "mount /dev/mapper/<unique label> /mnt/<path>"

---

### Post by 0f4d0335 on 2024-07-01
Just adding this in case you're using a desktop, these operations can be done in your GUI using the Disks utility.

---

### Post by Old Jimma on 2024-07-01
Hi 0f4d0335:

I had thought using disks was possible.... but cannot see how it can be done. After  selecting the Disk in the left column, and then what? The choices after clicking on "Addiitonal Partitions Options" does not give obvous options. Could you pease provide more specific guidance, please?

Thanks!
Old

---

### Post by Old Jimma on 2024-07-01
Totally right. Difficult for me, being pretty ignorant amout alot.

---

### Post by Old Jimma on 2024-07-01
You are right. See my last post to this thread that provides specific details and credits. Thank you!

---

### Post by Old Jimma on 2024-07-01
Hello Noble Numbat (perhaps, to be) Enthusiasts:

Thank all of you for your comments and support. You have kept the momentum going, and I have found "a soluiton." It may not be the one that "tweeks your gnome," but it seems to work so far, is easy for an ignorant person like me to set up, by using the existing Disks gui. Credits (and blame) go to the respondent who had incidentally, the snapiest name:  **0f4d0335**. And thanks to everyone else, and especially TheFu who has partiular deep knowlede of things, and continues support.. thank you!

[B]
A solution to encrypting an existing external drive after installing a fressh Ubuntu version[/B]

I found some details on what do to from this web site: [HTML] **https://askubuntu.com/questions/500981/how-to-encrypt-external-devices** [/HTML]

Specifically, here is a gui solution to Encrypting an existing partition, lifted from that web site:
Encrypting an existing partition

    • Open the Disks app
    • Select the partition that you want to get encrypted 
    • Make sure that it is not mounted by pressing on the square "stop" button 
    • Click the "gear" icon under the partition and choose Format... 
    • Select:  Internal disk for use with linux systems only (LUKS + Ext4) 
    • Check the password protect check box
    • Enter a name to distinguish the partition 
    • Enter your LUKS passphrase to encrypt it and confirm it

After this system completes you'll see from the Disks utility that the partition is designated as being LUKS.... a very gratifying thing to see.

Thanks to all for your advice
Old from the Old Country

---

