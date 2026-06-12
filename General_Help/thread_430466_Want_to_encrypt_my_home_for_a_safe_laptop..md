---
title: "Want to encrypt my /home for a safe laptop."
date: 2007-05-02
forum: General Help
---

### Post by musther on 2007-05-02
I've just got a new laptop, a Toshiba A100/E00 which works flawlessly with Ubuuntu 7.04!  I want to set it up with an encrypted /home partition so that if the unthinkable happens (it's stolen) then my personal info will be safe.

I have a couple of criteria for the method.

1 - The method of authentication and decryption should be my login, upon login the /home should be decrypted using my user password (or something similar to this).

2 - The method has to be fairly standard, such that if something horrible happens to the laptop hardware, I can whip out the drive, plug it in somewhere else, mount it, enter the password and get off the data.

I know there have been several how-to's and are methods posted on the web, and there may be pages on the wiki but I've failed to find them.  What I want to know is what method is good?

My /home is a separate partition, I would like to encrypt the whole thing.

Thanks

---

### Post by carl0ski on 2007-05-02
try TrueCrypt

[http://www.truecrypt.org/](http://www.truecrypt.org/)

i havent used it on an entire partition before however i have used it for folders in Windows and Linux.

It is supported by the linux kernel so no reason entire /home can't be encrypted

---

### Post by musther on 2007-05-02
Ok, TrueCrypt seems a good solution.  And I can create and mount truecrypt volumes.

Now, I want to create the volume /home/user-crypt which can be mounted as /home/user and used as the home directory. 

Now I need to figure out how to mount the encrypted volume automatically when I log in.  I think I need to use pam_mount, but I'm not sure how.

Anyone?

---

### Post by michux on 2007-05-07
Here is a howto that you may be interested in:

[http://polishlinux.org/howtos/encrypted-home-partition-in-linux/](http://polishlinux.org/howtos/encrypted-home-partition-in-linux/)

It covers configuring encrypted home partition and auto-mouting them upon log in. Hope it helps.

---

### Post by 50words on 2007-05-07
I use truecrypt. Here are a couple of tutorials that should help you through the installation:

[http://del.icio.us/50words/truecrypt](http://del.icio.us/50words/truecrypt)

I set up launchers for "TrueCrypt mount H" and "TrueCrypt unmount H" that sit on my panel. (I don't encrypt my actual /home directory, but I have a shared partition with Windows that I encrypt.) I don't want it to decrypt with my login for that extra layer of security. And Windows shared the partition, so it needs to have a separate logon. Plus, I want my logon for my encrypted partition (which has confidential client files) to be longer and more difficult, while my main login isn't all that important, so it is shorter and I can type it more quickly.

To mount:

```
sudo truecrypt -u /dev/sda3 /mnt/
```

To unmount:

```
sudo truecrypt -d
```

There is a GUI for it somewhere, but if you only have one encrypted partition, the command line is really all you need.

---

### Post by michux on 2007-05-26
There is another tutorial here: [TrueCrypt Tutorial: Truly Portable Data Encryption](http://polishlinux.org/howtos/truecrypt-howto/) -- it is a continuation of the tutorial for DM_Crypt explaining the steps to achieve home drive encryption with full automacy, but this time with TrueCrypt.

---

### Post by musther on 2007-07-06
In case anybody is still monitoring this thread (or anybody reads in the future), what I eventually did was use encfs and pam-encfs.

Encfs allows you to choose a folder, encrypt it, and mount it to another, for my laptop, I have done this.

Created /home/me/.encrypted and /home/me/encrypted

.encrypted stores the encrypted data, and encrypted is where it's mounted to for access.

I've copied important things, and things I want to be secure to encrypted, which encrypts them and places them in .encrypted.

I have then made links back to where they should normally be.

For example, to keep my firefox stuff safe, I copied .mozilla into encrypted (while it was mounted) and then linked back to it from /home/me/.mozilla (it's original location so that firefox can still find the files).

.encrypted is mounted to encrypted when I log in, all the links then work, and everything i've chosen to encrypt (by linking into the encrypted folder) is encrypted.

Anyway, here is a tutorial on using encfs and pam-encfs, just adapt it to your needs:
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by drpaul on 2007-07-07
Thanks for the follow-up. This is something most notebook users should do. [and I will as soon as I do a decent backup :-)]

Paul

---

