---
title: "Encryption, after installation, of home"
date: 2013-12-28
forum: General Help
---

### Post by vajorie on 2013-12-28
I've got a small SSD as a gift (first world problems....) into which I cannot fit all my files, so I decided to spread my stuff over two hard drives... How do I go about encrypting them after the move? 

I'm using Ubuntu 12.04 and am unsure whether (and how) to go with lvm or ecryptfs. Lvm seems better supported by multiple distros? 

Here's the setup; nothing is encrypted right now: 

SSD: 
/dev/sda1 -> /
/dev/sda2 -> /home

Hard Disk (connected with an optical hard drive caddy; mounted by fstab on boot):
/dev/sdc1 -> /HDD

/HDD has three folders in it: 
/HDD/Pictures
/HDD/Videos
/HDD/Music

and they are linked to /home as symlinks: 
/home/user/Pictures (symlink) -> /HDD/Pictures
/home/user/Videos (symlink) -> /HDD/Videos
/home/user/Music (symlink) -> /HDD/Music

What should I do?

Edit: I would like to do this without having to reinstall Ubuntu. Thanks in advance!

---

### Post by jjmarc on 2013-12-28
[SIZE=3]**Before you do anything, MAKE A BACKUP! **[SIZE=2]While it is unlikely that something will go wrong, it is possible, so make sure you have something to fall back on.[/SIZE]
[/SIZE]Just FYI, Ubuntu uses eCryptfs to encrypt folders, so the first thing you will have to do is install those utilities using this:
```
[FONT=Verdana][COLOR=#333333]sudo apt-get install ecryptfs-utils cryptsetup
```[/COLOR][/FONT]
[FONT=Verdana][COLOR=#333333]Next, make another user with admin (sudo) privileges. This is because you can't encrypt your home directory while you're logged in. Then, log off completely with your user and log in with the user you just made and run this:
```
[/COLOR][/FONT][FONT=Verdana][COLOR=#333333]sudo ecryptfs-migrate-home -u user
```[/COLOR][/FONT]
[FONT=Verdana][COLOR=#333333]Make sure to replace the word "user" with your regular account username (the one you just logged out of).[/COLOR][/FONT]
[FONT=Verdana][COLOR=#333333]After running this, you will be presented with some important notes.[/COLOR][/FONT]
[FONT=Verdana][COLOR=#333333]Make sure to read them. After doing this, &#8203;[B]immediately log off and log on as your regular user. DO NOT REBOOT!!!
[/B]After logging on, you will be presented with a dialogue box talking about recording your encryption passphrase. Click the "Run this action now" button and enter your password. You will then be shown your passphrase. Write it down and store it someplace safe because you'll need it if you need to recover your files in the future. You can also use the command
```
[/COLOR][/FONT][SIZE=2]ecryptfs-unwrap-passphrase[/SIZE]
```
to view this passphrase.

Now you'll need to encrypt your swap directory. Run the code
```
[COLOR=#333333][FONT=Verdana]sudo ecryptfs-setup-swap
``` but note that **THIS COMMAND WILL BREAK THE HIBERNATION FEATURE ON YOUR COMPUTER. **The suspend/resume capabilities will not be affected.

Now you can restart your computer to make sure everything works. If it does, you can remove the other user and backup home files in your home directory.[/FONT][/COLOR]

---

### Post by vajorie on 2013-12-29
Thanks for the quick reply! 

I had previously looked at the documentation for ecryptfs and had my home directory encrypted with it prior to this move. I was very annoyed by it not being portable (eg during the move, I couldn't figure out a way to decrypt it using other distros, nor ubuntu itself, the way one decrypts a truecrypt volume --easy and simple). 

Do you know how ecryptfs will handle the folder /HDD outside of my /home directory that is symlinked to /home/user/HDD? 

What do you think my other options are for this kind of setup? 

PS. I don't expect much from encryption except denying access to my files to a thief in case my laptop is stolen.

---

### Post by jjmarc on 2013-12-30
You're welcome. And now on to the questions!

1. I don't believe ecryptfs is designed to decrypt drives once they have been encrypted, which makes it more secure should someone be trying to access your information. However, that can cause an inconvenience to the user who encrypts their drive.

2. No, I do not. I typically encrypt my home folder, and if I need more space, I grab my files with the encryption passphrase and put a new hard drive in. :lolflag:
3. I haven't really researched other options because ecryptfs does what I need it to do and I have no need for anything else. 

Cheers,
jjmarc

---

