---
title: "LAMP on a desktop"
date: 2006-11-22
forum: General Help
---

### Post by sddfdds on 2006-11-22
I want to have a server behind my basic desktop, nothing huge, just a small site for friends and whatnot, so the whole GUI performance thing is a non-issue. It seems I have 2 options:

1) Auto LAMP install, then apt-get ubuntu-desktop

2) Desktop install, then apt-get apache2 php5-mysql libapache2-mod-php5 mysql-server

#1 does seem to be easier. It seems that there must be some underlying config stuff that goes into Auto-LAMP that goes beyond just apt-getting the things (or maybe I'm just wrong about that) so quickly popping the desktop on the server would appear to just work. There's just the question of the kernel and how different it is from the desktop. Are there any significant differences that might somehow interfere with the desktop?

Thanks

---

### Post by Average Joe on 2006-11-22
I have chosen option #2 myself. But I only use my webserver for development, so it is only accessible from my own computer. And I don't have mysql installed.

I am not sure if an auto LAMP install will configure everything correctly for you. Besides, I didn't mind tweaking my Apache configuration a bit myself.

In the end I don't think it really matters what option you choose. As far as I know the kernels of the desktop and the server install are the same, so you should roughly end up with the same system anyway.

---

### Post by sddfdds on 2006-11-22
Thanks, but the "roughly" is what I'm trying to get to the bottom of.  (And also possibly what the specifics are of the Auto-LAMP install)

---

