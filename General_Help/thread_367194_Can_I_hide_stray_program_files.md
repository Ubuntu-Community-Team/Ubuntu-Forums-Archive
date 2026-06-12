---
title: "Can I hide stray program files?"
date: 2007-02-21
forum: General Help
---

### Post by Dave54 on 2007-02-21
I'm trying to figure out the ubuntu file system (I'm switching from windows). It seems that "/home/dave" (my user name is dave) is the "home" folder, like windows' "my documents", except the desktop folder is in there, and a few other differences.

So I guess I'm supposed to use "/home/dave" for all my documents and stuff. There seems to be a LOT of program files/folders in there already, but luckily they're hidden. Now I run into a problem.

Sometimes programs put files in my "home" directory that aren't hidden. Moreover, they seem to be necessary for the program to function correctly. My question is this: Is there any way to hide or move these files without changing their name or location so that the programs that use them will still work correctly?

At the moment I have one program file in there: "GoogleEarthLinux.bin". I have discovered, however, that over time more and more will show up.

Please tell me if there is a different folder I'm supposed to use to house my files or any other solutions you come up with.

Thanks!
-Dave

---

### Post by zanglang on 2007-02-21
Actually, if you own the computer you could've installed the programs using an administrator account so the files get copied into a global directory like /usr/bin. That would be something like "sudo ./GoogleEarthLinux.bin", where you have to type your admin password. Also, most .bin files, like the Google Earth one, are just installation programs (think 'setup.exe') that you can safely delete or backup somewhere after you're done with them. ;)

So, what's usually done is:
- install programs with apt-get where possible, and use sudo to manually install
- documents, music, photos etc can have their own folder in home, like Windows' My Documents has My Music etc.
If you want your files accessible by all users, put them in a publicly read/writable folder, like /files/music etc.

For your 2nd question, you can hide files and folders in Nautilus using a .hidden file. [http://linux.about.com/library/gnome/blgnome6n6r.htm](http://linux.about.com/library/gnome/blgnome6n6r.htm)

---

### Post by bionnaki on 2007-02-21
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Dave54 on 2007-02-22
Thanks guys.

I did some research on .bin files. Since it wasn't a deb, rpm, or tar.gz, I didn't recognize it. I think that appeared because of automatix.

I still think some program files pop up in my home folder from time-to-time, but now I have the .hidden file to hide them if I have to.

Thanks for clearing up my questions.
-Dave

---

