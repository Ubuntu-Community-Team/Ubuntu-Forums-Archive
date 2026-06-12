---
title: "Duplicate sources.list entry"
date: 2012-12-08
forum: General Help
---

### Post by CaptainThunderwolf on 2012-12-08
Hola, forumites. The name's CaptainThunderwolf, and I've got a problem. Well, lots, actually, but only one that I'm specifically requesting help for at the moment. You see, whenever I enter Terminal and input the command, "sudo apt-get update", I get an error message saying "W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages)", which shows up about, oh, four or five times in a row (Or else several other, very similar looking error messages, I suppose). As a bit of a Linux newbie (Had it for years, but I don't know much about its real intricacies), this understandably both confuses and alarms me. I've looked up a handful of other forum postings regarding this, and apparently it has something to do with duplicate entries in the sources.list folder or something (Like I said, I'm a newbie). So, does anyone have a recommendation? I've got a few other bugs I'm working out right now, but this one's by far the most scary looking, so I'd really appreciate some help.

---

### Post by sammiev on 2012-12-08
Hi, You can use gedit or ubuntu tweak to edit your source list to remove the duplicate. Ubuntu Tweak is very easy to use. :)

---

### Post by CaptainThunderwolf on 2012-12-08
So after I download it, I guess I use the "Janitor" utility and it removes excess files, extraneous files, duplicates, et cetera? And I can go to the Source Editor to...edit the source files?

---

### Post by ibjsb4 on 2012-12-08
You already have Software Sources loaded, its part of the default install.  Just use it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

