---
title: "Using windwos fonts in linux"
date: 2007-10-20
forum: General Help
---

### Post by enchance on 2007-10-20
How do I import all 1,500 of my windows fonts? And since I'm using DreamWeaver in WINE,will they all be detected also? Or do I have to install them twice: first for linux, second for WINE?

---

### Post by Sunforge on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=452134](http://ubuntuforums.org/showthread.php?t=452134)

Quoted from the above link (thanks to BrowneR), with some minor edits for clarity, I hope.

First make yourself root
sudo -s

Create a directory to hold the fonts (as root):
mkdir /usr/share/fonts/truetype/msfonts
(fonts in here are available to all)

Copy the font(s) into the newly created directory:
cp [fonts] /usr/share/fonts/truetype/msfonts

[fonts] being the windows volume you've mounted, all fonts are stored in windows\fonts if you're using XP.

Run the following to recreate the font cache:
fc-cache -f -v

That'd get you up and running in nix, but you'd have to repeat the process to get everything working in wine, copying the fonts to the wine/windows/fonts directory to get everything working for you. I can't guarantee that's the case as I'm not a wine user.

---

### Post by MalcolmSP on 2007-10-21
> 
Copy the font(s) into the newly created directory:
cp [fonts] /usr/share/fonts/truetype/msfonts


I tried doing this and I get a ```
 cp omitting directory
``` error and nothing happens. My [fonts] have been copied over to a flash drive. I also tried copying them from a file folder on my desktop with the cp command, and that did not work either. I also tried copying them by drag and drop into the new directory and got an permission error. Other ideas about what I might be doing wrong?

---

### Post by Maestro23 on 2007-10-21
The directory /usr is owned by **root. ** You need root privileges.  Use the **sudo** command in front of your copy command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MalcolmSP on 2007-10-21
I do that and I get the following:
[code]
sudo cp /media/disk-1/Fonts /usr/share/fonts/truetype/msfonts

cp: omitting directory `/media/disk-1/Fonts'
[\code]

---

### Post by steveneddy on 2007-10-21
Go to your /home folder and make a folder named

```
.fonts
```

the dot (.) has to be in front of the file name because it is a hidden file.

Put all of your Windows fonts there and you can aaccess them is Open Office or any other app that needs fonts.

Make sure that you restart.

:popcorn:

---

### Post by Foster Grant on 2008-02-29
> **Sunforge said:**
> [http://ubuntuforums.org/showthread.php?t=452134](http://ubuntuforums.org/showthread.php?t=452134)

Quoted from the above link (thanks to BrowneR), with some minor edits for clarity, I hope.

First make yourself root
sudo -s

Create a directory to hold the fonts (as root):
mkdir /usr/share/fonts/truetype/msfonts
(fonts in here are available to all)

Copy the font(s) into the newly created directory:
cp [fonts] /usr/share/fonts/truetype/msfonts

[fonts] being the windows volume you've mounted, all fonts are stored in windows\fonts if you're using XP.

Run the following to recreate the font cache:
fc-cache -f -v

That'd get you up and running in nix, but you'd have to repeat the process to get everything working in wine, copying the fonts to the wine/windows/fonts directory to get everything working for you. I can't guarantee that's the case as I'm not a wine user.

This is (slightly) incorrect. It needs a recursive modifier.

So that would be ...

cp -r [fonts] /usr/share/fonts/truetype/msfonts

Then reboot and you're golden. :guitar:

---

