---
title: "Help With Installing Java On Ubuntu Dapper Server"
date: 2006-10-09
forum: General Help
---

### Post by Brian L on 2006-10-09
I have been through several threads explaining how to install Java  on Ubuntu desktop, but none for server. I guess it's expected that if you choose Ubuntu server that you should know how to do theses things, but alas, I do not :(.

---

### Post by handy on 2006-10-09
Is there any reason why you can't install it as you would on a workstation?

[Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation") has **2 Java install options** in it's menu.

All the best... :)

---

### Post by Brian L on 2006-10-09
I'm not sure. I tried to but it didn't seem to work.

---

### Post by lemonsCC on 2006-10-09
You tried Automatix or the repos?  EasyUbuntu installs it as well.

[EasyUbuntu]("http://easyubuntu.freecontrib.org/index.html")

[Automatix]("http://getautomatix.com/")

---

### Post by Brian L on 2006-10-09
I did try AutoMatix but when I run "automatix2" I get this error:

GtK-WARNING **: cannot open display

Pretty sure thats because I don't have a display, this being a server >.>

---

### Post by lemonsCC on 2006-10-09
Oh..that could be why.

Here are directions for the command line.

[UbuntuGuide.org]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_JRE_v5.0_Update_8")

---

### Post by Brian L on 2006-10-09
See, I've seen this before. 

I've done this:

sudo chmod a+x jre-1_5_0_08-linux-i586.bin
sudo ./jre-1_5_0_08-linux-i586.bin

I don't think I need this because I don't have Firefox, and don't need it to work with Java:

cd /usr/lib/firefox/plugins

And I'm not sure which of these commands to execute (currently trying them out)

sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
cd /usr/lib/mozilla/plugins
sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so

/me goes back to PuTTY

EDIT: hmmmm. I cant seem to mkdir in /usr/ like it says in the tut. It says it is a read only file system.

---

