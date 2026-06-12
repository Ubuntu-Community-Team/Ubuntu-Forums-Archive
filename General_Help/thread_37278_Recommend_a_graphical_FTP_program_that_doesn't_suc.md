---
title: "Recommend a graphical FTP program that doesn't suck"
date: 2005-05-26
forum: General Help
---

### Post by mostwanted on 2005-05-26
gFTP is really bad IMO. Multiple selection is faulty, speed is bad, it constantly times out so you have to re-login and it doesn't save passwords, so you have to type them all the time and I'm sure there are other wrongs with it.

I've been forced to wine FileZilla which is an excellent Windows ftp program. And it works great, but feels a little awkward to use because of some graphical flaws in wine.

So I'm looking for a FileZIlla-like linux ftp-client. Any recommendations?  Preferable dpkg'able or apt-get'able.

---

### Post by tread on 2005-05-26
I remember using some program under kde .. I think it was called kbear. Its pretty nice .. 
I wish I was on Linux to confirm this, but there is an applet you can use that mounts remote directories so you can just browse them like other folders. At least, it works for sftp.

---

### Post by ntd on 2005-05-26
Have you tried the Linux Builds of FileZilla (v 3 IIRC) yet?

I haven't used them yet, but they've been releasing nightlys for about 6 months, so I'm sure there is some progress

[http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

Edit:  Just want to say that I tried it tongiht when I got home from work...it actually works pretty well!  Give it a shot (it is ALPHA btw, so beware)

---

### Post by Orunitia on 2005-05-26
[QUOTE=mostwanted]gFTP is really bad IMO. Multiple selection is faulty, speed is bad, it constantly times out so you have to re-login and it doesn't save passwords, so you have to type them all the time and I'm sure there are other wrongs with it.[/QUOTE]

gftp does save passwords. Try bookmarking and it will ask you if you want to save the password. From then on just choose the ftp server from your bookmarks list. "Speed is bad, it constantly times out" sounds like a problem with the server, not gFTP.

---

### Post by joele on 2005-05-26
[QUOTE=Orunitia] "Speed is bad, it constantly times out" sounds like a problem with the server, not gFTP.[/QUOTE]

Agreed, I have also always found gftp to be reliable...

---

### Post by jeremy on 2005-05-27
I too have always found gFTP to be very fast and reliable.

---

### Post by Rnd227 on 2005-05-27
Without being a fan of gftp, I've never experienced any major trouble with it, and it certainly does save passwords.

Otherwise, I've been using Krusader (ugly as hell, but reliable) or just mounted distant servers as folders.

---

### Post by mostwanted on 2005-05-27
[QUOTE=Orunitia]gftp does save passwords. Try bookmarking and it will ask you if you want to save the password. From then on just choose the ftp server from your bookmarks list. "Speed is bad, it constantly times out" sounds like a problem with the server, not gFTP.[/QUOTE]

There is no "problem with the server" when using FileZilla in Wine curiously enough...?

I'm gonna try the Linux FileZilla. I had no idea they'd started making a Linux version.

---

### Post by mostwanted on 2005-05-27
Okay I've installed Filezilla 3 - Here's a screen:

[http://www.htmldesign.dk/img/screens/Filezilla3_ubuntu.png](http://www.htmldesign.dk/img/screens/Filezilla3_ubuntu.png)

Looks good at least, but it has some quirks being Alpha and all :) but so far it's been a better experience than gFTP that's for sure.

---

### Post by enric on 2005-05-27
[QUOTE=mostwanted]gFTP is really bad IMO. Multiple selection is faulty, speed is bad, it constantly times out so you have to re-login and it doesn't save passwords, so you have to type them all the time and I'm sure there are other wrongs with it.

I've been forced to wine FileZilla which is an excellent Windows ftp program. And it works great, but feels a little awkward to use because of some graphical flaws in wine.

So I'm looking for a FileZIlla-like linux ftp-client. Any recommendations?  Preferable dpkg'able or apt-get'able.[/QUOTE]
 You already have it.  Just enter the ftp url in nautilus, and drag your files.

---

### Post by betrayed on 2005-05-27
Well if you don't mind apps for kde you could try kftpgrabber.  Works very well here.  Found it to be good replacement for flashfxp from windows land

---

