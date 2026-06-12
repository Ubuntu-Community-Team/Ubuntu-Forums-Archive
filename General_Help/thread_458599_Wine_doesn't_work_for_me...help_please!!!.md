---
title: "Wine doesn't work for me...help please!!!"
date: 2007-05-29
forum: General Help
---

### Post by bishop9226 on 2007-05-29
I installed the latest wine via automatix.  

> art@art-desktop:~$ which wine
/usr/bin/wine
art@art-desktop:~$ 


also $ winecfg gives me the wine tabs.

But for EVERYONE else ive talked to, when they install wine, all they have to do is click on an exe file and do "open with" wine and it opens the exe and loads the wine wrapper!!!! but for me wine DIDNT install ANYTHING in my applications menu and when i click on exe files i get the "no suitable application error"

> Cannot open /media/sda1/utorrent.exe: No application suitable for automatic installation is available for handling this kind of file

so it is acting as if there is NO wine at all.  so i am reading through the wine documentation and according to it, I should be able to use a gui called WINEFILE that came with wine but i cant find this anywhere. It also says if i do 

> art@art-desktop:~$ wine c:\\utorrent.exe
wine: cannot find 'c:\utorrent.exe'
art@art-desktop:~$ 


i can run progs via wine from the cmd terminal, but UTORRENT IS IN MY C DRIVE, IM LOOKING RIGHT AT IT ON MY NTFS PARTITION, drive that linux calls sda1 is my C drive in windows, and utorrent is RIGHT THERE.  

so not only do i get NO menu or OPEN WITH for wine, i cant even get things to work in the command terminal!!!

 it worked easily for this guy:

> Look i'm using uTorrent under wine right now.

It was very easy to make it work. Actually i didn't do anything

I don't know if this is the bet way to do this, but i tell you what i did.

I installed wine using Automatix, so maybe that's the right path.

Then i went in my windows partition with Krusader (a file manager), right clicked on uTorrent, which was alredy installed in my windows xp, and selected Wine in the "open with..." menu.

That's it. It simply worked.  ([http://ubuntuforums.org/showthread.php?t=381786](http://ubuntuforums.org/showthread.php?t=381786))

someone please help me:(

---

### Post by Crafty Kisses on 2007-05-30
To be honest, Automatix is not the best thing to use while installing Wine.

---

### Post by hikaricore on 2007-05-30
Also using winecfg to configure another drive other than ~/.wine/drive_c as C: probably isn't the best thing to do.

This "drive_c" contains specific files wine needs to work properly in most situations.

Unless of course you didn't do this, then there is the solution to your problem as your ntfs partition is not drive C: .

---

### Post by Crafty Kisses on 2007-05-30
That's well said.

---

### Post by zvacet on 2007-05-30
Right click on icon>open with>scroll down and you will see use specific command(or something like that I don´t use english version)>search box>/usr/bin/wine


You can do it this way:

Put utorrent exe in any folder(let say it is programs)

```
wine /home/your_user_name/programs/utorrent exe
```

---

