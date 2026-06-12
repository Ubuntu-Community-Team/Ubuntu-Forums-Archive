---
title: "How to run OziExplorer in Dapper?"
date: 2006-07-13
forum: General Help
---

### Post by ruiruas on 2006-07-13
Oziexplorer3d is "an add-on" to Oziexplorer. It creates 3D images of maps with height data from various sources. Oziiexplorer runs well with Wine, but the 3D app doesn't.

I've tried running it with wine, but it fails to run. The program installed, but when I do: "wine OziExplorer3d.exe" it returns:

err:seh:setup_exception nested exception on signal stack in thread 000b eip b7eab50a esp 7fe45120 stack 0x7fa81000-0x7fb90000

Can anyone help my? (I know nothing about programming...)

Thanks in advance,

---

### Post by ruiruas on 2008-01-13
In gutsy, with the new version of wine, both OziExplorer and Ozi3d work "out of the box". Ozi3d still shows some inconsistency, but it renders the images and almost every function works. The buttons disappeer though...

---

### Post by Rhubarb on 2008-01-13
Try getting the latest wine from here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Follow the instuctions to get the wine repositories.

Then update your system
System --> Administration --> Update Manager.

It'll automatically download the latest verion of wine.

Once updated, you may have delete your ~/.wine directory (make sure it's backed up 1st), then re-install the programs.

You may have to fiddle with some of the wine settings too
In a terminal, type in
```
winecfg
```
And change it to win xp / 98 / 2000.

---

