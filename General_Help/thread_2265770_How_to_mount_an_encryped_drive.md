---
title: "How to mount an encryped drive?"
date: 2015-02-17
forum: General Help
---

### Post by mn_voyageur on 2015-02-17
Okay.  So, I did a fresh install of 14.04.

I have the drive that was loaded with v12. 

My personal folder was encrypted. I have the password and the passphrase.

When I drill down on the v12 HDD, I get to "Access-Your-Private-Data.desktop."  When I double click, it appears to try to open a terminal, which is promptly closed.

I tried running "ecryptfs-mount-private" from the terminal, as instructed in the README.txt file, with no luck.

So, how do I access my personal files?

Thanks,
MarkN

---

### Post by corbin.loftis on 2015-04-21
This may be a little late to help, but if you want to recover and open an eCryptfs directory (like an encrypted home folder), you need to open a terminal and type:

[sudo ecryptfs-recover-private]

This will then prompt for a password to your login and search for any encrypted directories. If you already know the path to the encrypted directory, then type it after the previous command:

sudo ecryptfs-recover-private /home/.ecryptfs/USERNAME/.Private

This way, it will bypass searching for the directory. After it finds it, ecrypt will prompt and ask if you would like to recover, and then your login password (that is associated with the encrypted home folder). Once you type these in, it will mount the encrypted home folder in /tmp/media/. Navigate there in root nautilus and you can access all of your files.

---

