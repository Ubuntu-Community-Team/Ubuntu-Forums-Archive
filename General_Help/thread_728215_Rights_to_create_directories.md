---
title: "Rights to create directories"
date: 2008-03-18
forum: General Help
---

### Post by bioShark on 2008-03-18
Hi

I have recently installed kubuntu 7.10. I have created a directory for downloading stuff in /home, and I set firefox by default to download everything there. Also Asureus has the same path for downloading. 
Well it seems firefox won't download anything there, i needed to change him to put them on the deskop. Asureus gives an error that it can't create folder in that directory, so I needed to change the path to /home/.azureus.

My question is: Is this normal? I mean I am root.....


thanx

---

### Post by taurus on 2008-03-18
You are not root!  There is a root account and you are just a regular user who happens to have a root privilege.  That's why you can use sudo/gksudo with your own password.

If you need to write outside of your $HOME, then you either need to change the permissions of that directory (don't do that blindly or you could trash the whole system) or use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bioShark on 2008-03-18
Ok, I did it. I changed the permmission on the whole directory tree. But I was under the impression that the user I have created is actually the root. Because at the first run of kubuntu I actually wanted to log in as root but it didn't let me, so maybee I misspelled the password and that's why it didn't let me log in. I'll check that.

---

### Post by bodhi.zazen on 2008-03-18
First, welcome to Ubuntu.

Second, love the avatar.

Third, "I changed the permmission on the whole directory tree." is not such a good idea and is both a security risk.

I suggest you re-install and take a look at the link taurus provided.

---

### Post by bioShark on 2008-03-18
Hi Bodhi

First: Thanks for the greetings, Its my second try with Ubuntu, first one ended a few months ago because of 3rd party involvement. Now I am here to stay.

Second: I am a huge fan of Dune. Is your nick-name inspired by any chance from Baldurs Gate 2?

Third: I am no n00b to IT, in fact I am a Software developer, so I know a few things about permissions (not on Linux so much, but still). Regarding security issues, there are none: I alone use the PC. I have a strong Router Firewall...so...

About re-install, do you mean the whole system? Kubuntu again? Well it wouldn't take more then 20 minutes, but I will first read the link you suggested anyway. In fact this installation of Ubuntu is so to say a Sandbag for me to study, to be ready for next months release, so I don't care if I scrwe the system up :) (There's only one way to learn I always say). But there might be a reason for which I would re-install kubuntu:

If I don't find an answer to the problem I've posted in this thread:

[http://ubuntuforums.org/showthread.php?t=727096](http://ubuntuforums.org/showthread.php?t=727096)

Really appreciate if you can help me with that one, even if I do or not a re-install. Because it bugs me not knowing what the problem is.

Thx

---

