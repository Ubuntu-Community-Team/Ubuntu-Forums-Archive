---
title: "Forgot password, locked out!"
date: 2007-06-15
forum: General Help
---

### Post by bokorpop2 on 2007-06-15
I have not logged into Uubuntu or these forums for a few weeks, and now realized that I have forgotten my username and password for logging into Ubuntu. Since I remember using the same password for these forums, I also cannot login to the forums using my origial handle, which was was "bokorpop". Is there anyway I can recover my password for my handle "bokorpop" on these forums. So far, I can only get it so that I can reset my old password, but I dont want to reset it, I need to know what it is so I can log into Ubuntu.

If I cannot recover this password, I am totally screwed, as there was some very valuable data on my Ubuntu partition that cannot be accessed from when I boot into Windows. help much appreciated!

---

### Post by ashz on 2007-06-15
Sure ask them nicely for the MD5 encrypted hash of your password and ill tell you what it is in a few mins :P 

In the grub menu when you boot select recovery mode this will boot you up to a root prompt, without the need to put in a password then just type...

passwd username

where username is ur username

that should work...i think :P

---

### Post by wconstantine on 2007-06-15
You should be able to recover your data from Linux through Windows. You can browse into EXT2/EXT3 filesystems using the program explore2fs.
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
If you use reiserFS you can use the program called yareg.
[http://yareg.akucom.de/](http://yareg.akucom.de/)

It's just to google and you'll likely find an app that allows you to browse whatever filesystem you run in Windows.

Search on "browse <filesystem> windows" and I think you will find something for any common filesystem. You should be able to get files without entering passwords from your Linux partition.

I think that a proper PM, with some kind of identification, to a moderator on the forum could make you get your pass back aswell.

As far as I know there ain't any known way to bypass Ubuntu login screens but I could mention dousens of way to do it for Windows if you want! :P

Anyways. I hope I helped. Good luck!

---

### Post by bokorpop2 on 2007-06-15
as a noob, I dont want to mess with these strange programs. I will first try asking a moderator, but where/ how do I contact one?

If that doesnt work I will try the reset thing and get back to you later if it woks. Thanks for the advice so far

---

### Post by smoker on 2007-06-15
> **bokorpop2 said:**
> as a noob, I dont want to mess with these strange programs. I will first try asking a moderator, but where/ how do I contact one?

If that doesnt work I will try the reset thing and get back to you later if it woks. Thanks for the advice so far

you could try here: [http://ubuntuforums.org/index.php?page=about](http://ubuntuforums.org/index.php?page=about)

best of luck

---

