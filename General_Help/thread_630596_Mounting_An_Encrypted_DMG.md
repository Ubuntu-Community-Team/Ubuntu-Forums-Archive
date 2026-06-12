---
title: "Mounting An Encrypted DMG"
date: 2007-12-03
forum: General Help
---

### Post by adese on 2007-12-03
I keep my music on an encrypted (AES-128) .dmg file on an external firewire hd to my Mac. My mac is dual boot (Ubuntu 7.10 & OSX 10.5). I'm having trouble mounting the image in Ubuntu tho. 

After much searching round and trial and error I found the command that works :

> sudo mount -o Loop -o encryption=aes -o keybits=128 -t hfsplus /media/xternal/Music.dmg /mnt/Music


However when I input my password for the image it returned :

> Error Password must be at least 20 characters

So I re-encrypted the .dmg with a 20char password. However when I tried to mount it this time it returned : 

> ioctl: LOOP_SET_STATUS: Invalid argument, requested cipher or key length (128 bits) not supported by kernel

I have installed loop-aes-utils and cryptsetup but no avail. 

Any help would be awesome.

---

### Post by someonestolecc on 2007-12-26
This affects me too.. I'm trying to open an encypted .dmg file from the past and get exactly the same thing... :( I don't want to have to borrow a mac :\

---

### Post by someonestolecc on 2007-12-26
I ran - modprobe cryptoloop which meant no error.

But after I entered the password I tried to mount -t hfs it and it said wrong file type.. what file type am I supposed to use??

---

### Post by juicymixx on 2008-02-29
***Error Password must be at least 20 characters***

Same problem... anyone have a solution for this one?   The encrypted .dmg opens fine on OS X.

# file e_disk.dmg 
e_disk.dmg: data

# modprobe cryptoloop
#
(no error)

# mount -o Loop -o encryption=aes -o keybits=128 -t hfsplus e_disk.dmg /mnt/mi
Password: 
Error: Password must be at least 20 characters.

???
I've tried dmg's with various different passwords; all less than 20 characters, but still long.   I always get this error.:confused:

---

