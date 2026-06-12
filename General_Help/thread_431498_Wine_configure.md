---
title: "Wine configure?"
date: 2007-05-03
forum: General Help
---

### Post by PricklySponge on 2007-05-03
I just installed WINE using

sudo apt-get install wine

But when I run

wine setup

I get a message that says

wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found

What do I do?

---

### Post by YokoZar on 2007-05-03
What are you trying to do?

winecfg will let you configure Wine, but which application are you trying to run?

---

### Post by ianprinz on 2007-05-03
After having installed wine through apt-get you just run "winecfg" in a console, alternatively access its configuration through "System settings>Advanced" if you run KDE or "Control Center" if you run Gnome. There you can specify what system wine should emulate i.e XP, 2000, Win98 etc, plus other settings that can improve compatibility and speed.

To install programmes just type wine + the path to the setup executable in a console. Beware that some programme will need some wine tweaking to make them work and/or install.

---

### Post by PricklySponge on 2007-05-03
Alright. I'll try this when I Get home. I'm trying to run Counter Strike Source, by the way.

Thanks for your help :)

---

### Post by PricklySponge on 2007-05-03
I have another question. To install steam I need to dll a font called tamoha. I have it saved on my desktop; how do I get to the wine folder that it needs to be in?

---

### Post by crispy_420 on 2007-05-03
Install font:

/home/username/.wine/drive_c/windows/fonts

or in english:

Go to home folder and hit control + h to show hidden folders.
Go to the wine folder (.wine).
Go through folder as you would in windows. So drive_c -> windows -> fonts
Put that font in there.

At least that is how it works in windows and since we emulating and it's file system it that should work.

---

### Post by PricklySponge on 2007-05-03
Alright, that worked. Thank you.

One last question :)  :

I have downloaded the steaminstaller ( its names Steaminstall.msi)
Is it supposed to be msi? 

Also, to open it with wine i'm right clicking it, and selecting "open with other application". Then I choose "custom command" and type in wine. Nothing happens. What am I doing wrong?

---

### Post by crispy_420 on 2007-05-04
Yes that is a standard of installer in windows just like an exe. As far as installing in wine:

[http://www.winehq.com/pipermail/wine-users/2005-December/020055.html](http://www.winehq.com/pipermail/wine-users/2005-December/020055.html)

---

### Post by PricklySponge on 2007-05-04
This is what i'm typing, and the feedback i'm getting. Wine doesnt start. Am I doing it wrong?

makee@makee-desktop:~$ /home/makee/AllDocs win msiexec /i SteamInstall.msi
bash: /home/makee/AllDocs: is a directory

---

### Post by PricklySponge on 2007-05-04
Also, if it happens to be a problem with WINE, it might be worth noting the the symbols next to wine functions in the application menu are the blank white ones with a a blue line at the top- if that means that is is broken or something.

---

### Post by uberushaximus on 2007-05-17
Try
```
msiexec /i /home/makee/AllDocs/SteamInstall.msi
```
 
But I always just use [http://steampowered.com/download/SteamInstall.exe](http://steampowered.com/download/SteamInstall.exe)

---

