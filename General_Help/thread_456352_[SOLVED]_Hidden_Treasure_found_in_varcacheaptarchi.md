---
title: "[SOLVED] Hidden Treasure found in /var/cache/apt/archives"
date: 2007-05-27
forum: General Help
---

### Post by Lutherian on 2007-05-27
Before I get too excited with my discovery.

Background: I have a slooooow internet connection, no caps, but slow.
One of the issues that have been bothering me for a while is - sure Ubuntu is great, but each time a download an application from a repo, I don't have a copy to keep. With windows, each application I downloaded was backed up on a CD or DVD to save me from having to re-download the file. 

I kept worrying - "what if my machine crashes" I really don't want to have to download all those apps again - it's taken me months to get the system setup the way I like it."

Just now I was installing an antivirus program but didn't apprear on my Gnome start menu and went hunting for it ... and stumbled across a /var/chache/apt/archives ....  Oh my...it full of .deb files

Is this a "backup" of all the software I've downloaded on my machine?
Could I burn these to DVD and use them If I need to reinstall via dpkg? :D

This could be really, really good news.

---

### Post by dagrump on 2007-05-27
Thats them, I copy them to an external hard drive.

---

### Post by drs305 on 2007-05-27
Yes, the deb files are archived here. If your sources list refers to the location of the deb files in var/cache/apt/archives or to a backup CD you can restore the programs without access to the internet.

---

### Post by PriceChild on 2007-05-27
```
apt-get clean
```will clean out this archive as it can get very big.

Tools like aptoncd will help you make cd repositories of it all.

---

### Post by Lutherian on 2007-05-27
It just gets better and better (^_^) Thanks for the confirmation all.

---

