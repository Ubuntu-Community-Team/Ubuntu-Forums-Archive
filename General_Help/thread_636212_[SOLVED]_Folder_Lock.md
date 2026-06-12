---
title: "[SOLVED] Folder Lock"
date: 2007-12-09
forum: General Help
---

### Post by LinuxIsInnovation on 2007-12-09
Is there a folder lock for Ubuntu Gutsy? Please provide me a debian package if possible..

---

### Post by p_quarles on 2007-12-09
> **sayakb said:**
> Is there a folder lock for Ubuntu Gutsy? Please provide me a debian package if possible..
You don't need any extra packages to "lock" a directory. It's not entirely clear from your question, though, what you're trying to do. Do you want to make the directory read-only? Do you want to make it completely inaccessible to non-root users? Do you want to encrypt it? I'm happy to give you a hand if you provide some more details about what you want to do.

---

### Post by LinuxIsInnovation on 2007-12-10
I want to block non-root users from accessing.. that is, complete locking. Only I as root can unlock it.

---

### Post by p_quarles on 2007-12-10
Easy enough. Open a terminal, and type the following:
```
sudo chown -R root:root /path/to/folder
```
That command will change ownership of the folder in question to root. To prevent anyone else from accessing it, enter this command:
```
sudo chmod -R 700 /path/to/folder
```
That command will prevent anyone other than the root account from even opening the folder. 

A couple things to keep in mind:
1) In order to use the "cd" command to enter this folder, you will first need to login as root:
```
sudo sh
```
Simply typing "sudo cd /path/to/folder" will not work.

2) Anyone who has physical access to this computer will still be able to log in as the root account and access this locked folder. If you need to prevent this, you will have to use encryption.

---

### Post by LinuxIsInnovation on 2007-12-10
Thank you...
That worked for me.. :)

---

### Post by LinuxIsInnovation on 2007-12-16
> **p_quarles said:**
> Easy enough. Open a terminal, and type the following:
```
sudo chown -R root:root /path/to/folder
```
That command will change ownership of the folder in question to root. To prevent anyone else from accessing it, enter this command:
```
sudo chmod -R 700 /path/to/folder
```
That command will prevent anyone other than the root account from even opening the folder. 

A couple things to keep in mind:
1) In order to use the "cd" command to enter this folder, you will first need to login as root:
```
sudo sh
```
Simply typing "sudo cd /path/to/folder" will not work.

2) Anyone who has physical access to this computer will still be able to log in as the root account and access this locked folder. If you need to prevent this, you will have to use encryption.

Using chmod isnt helping too much.. Isnt there anything that can password protect my folders?

---

### Post by p_quarles on 2007-12-16
> **sayakb said:**
> Using chmod isnt helping too much.. Isnt there anything that can password protect my folders?
What do you mean? In what way is it not working? With this setup, only root will be able to access that folder. 

I only know of two ways to password protect a directory. One is to zip it with password protection, but zip's security is relatively easy to break if a user knows what he's doing. The other is to move the folder into an encrypted disk image, which is extremely secure, but can be a bit of a hassle if you need to access the folder frequently.

---

### Post by LinuxIsInnovation on 2007-12-16
Actually, mine is a peculiar case.. I dont want my bro to access some files.. He knows my root password, so he can easily unlock them.. Thats why I wanted some separate software.. I'll try the zip method though.. encryption need not be strong in my case :D

---

### Post by p_quarles on 2007-12-16
Okay, I getcha now. If you're going to use the zip password protection, be sure to use the "-e" option and not the "-P" option. The latter will store the password in plain text, so is completely pointless for security. The former will prompt you for a password and won't echo it.

Also, since you're trying to lock these files and not save hard drive space, and I'd suggest using no compression. This will make zipping and unzipping the folder *much* faster. Something like this:
```
zip -e -0 documents.zip /home/username/important_files/
```
Good luck.

---

### Post by LinuxIsInnovation on 2007-12-17
root@Muzic-Jukebox:~# zip -e -0 test.zip /home/glade/Locker/
Enter password: 
Verify password: 
  adding: home/glade/Locker/ (stored 0%)
root@Muzic-Jukebox:~# 

I can still open the file thru nautilus :(

---

### Post by Green_Star on 2007-12-18
Can some one point me to a guide about making folder into an encrypted disk image?

---

### Post by stchman on 2007-12-18
> **sayakb said:**
> Is there a folder lock for Ubuntu Gutsy? Please provide me a debian package if possible..

If you want to keep other non-root users from even looking at your files in a particular folder just set the proper permissions.

If you are the owner then use the following command.  Note sudo not needed.

```
chmod -R 700 <folder you wish to lock including path>
```

This will keep out non-root users from even being able to open your files.  You will not be able to keep root from looking.

---

### Post by LinuxIsInnovation on 2007-12-18
Sir, the users know my root password and I cannot block their access as root. Please provide sumthing which is not dependent on the root pasword.

---

### Post by stchman on 2007-12-18
> **sayakb said:**
> Sir, the users know my root password and I cannot block their access as root. Please provide sumthing which is not dependent on the root pasword.

If the users know your root password there is no stopping them from accessing your files.  My advice is to change the root password.

Remember root can do anything.

---

### Post by p_quarles on 2007-12-18
> **sayakb said:**
> Sir, the users know my root password and I cannot block their access as root. Please provide sumthing which is not dependent on the root pasword.
Well, I use cryptsetup and losetup to create an encrypted virtual drive, but I cannot find a good online tutorial for that. It's easy to do, but there are quite a few steps for the initial setup. If you're curious, there's a step-by-step guide in the book _Ubuntu Hacks_, published by O'Reilly.

In any case, I found a decent tutorial on Truecrypt, which looks like it can do much the same thing. My advice is to give that a try:
[http://howtoforge.com/truecrypt_data_encryption](http://howtoforge.com/truecrypt_data_encryption)

> **stchman said:**
> If the users know your root password there is no stopping them from accessing your files.  My advice is to change the root password.

Remember root can do anything.
Umm, no. Root cannot read passphrase-protected AES encrypted filesystems. That's why it's so important to remember the passphrase: you lose that, and you lose your data.

---

### Post by LinuxIsInnovation on 2007-12-19
Thank you. This solved my problems to quite an extent. Thanx again. :)

---

