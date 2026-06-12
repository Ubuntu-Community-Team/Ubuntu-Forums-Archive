---
title: "Remove fonts from system"
date: 2015-03-20
forum: General Help
---

### Post by Alduins_Khajiit on 2015-03-20
I accidentally installed an extra font onto my Ubuntu system that I want to remove because of the mistake, but** EVERY** ANSWER ON THE INTERNET I found ARE LIES AND DO **NOT** WORK!!! **NONE** of these answers here: [http://superuser.com/questions/248844/how-do-you-remove-fonts-from-ubuntu](http://superuser.com/questions/248844/how-do-you-remove-fonts-from-ubuntu) were the truth!!! NONE SHOWED UP IN ANY OF THESE SO CALLED ANSWERS!!! the answers here: [http://askubuntu.com/questions/371213/how-to-delete-fonts-in-ubuntu](http://askubuntu.com/questions/371213/how-to-delete-fonts-in-ubuntu) WERE ALSO LIES!!! MY FONT DIDN'T SHOW UP NOR DID ANY OF MY MANUALLY INSTALLED FONTS!!!

I am at WITS END AND NEED SOME TRUTHFUL ANSWERS!!! (unlike all the other answers I found)

---

### Post by v3.xx on 2015-03-20
Fonts can be placed in several locations.  You just have not found it.  Do a file system search to locate your package.  

I see nothing wrong with the links you provided.

So I guess you will take this as a lie.

---

### Post by buzzingrobot on 2015-03-20
How did you install that font?  

 If you used a GUI tool to install the font, does that tool lack a deletion capabilty?   If you can't use that tool to delete the files, you will need to locate the folder they are in and delete it.

That said, font files are generally pretty benign things.  Beyond taking up a tiny bit of disk space and perhaps a menu entry or two, there's no harm done by leaving them alone.

Font files and folders in Ubuntu are typically located in /usr/share/fonts or in your home folder (/home/<YOU>/.fonts or /home/<YOU>/share/fonts.  Fonts, potentially, may also be in /usr/local/share/fonts.

Fonts consist of files that are collected in a folder that bears a name based on the name of that font.  E.g., on my system the Liberation fonts are in the folder /usr/share/fonts/truetype/liberation. If I wanted to remove the Liberation fonts, I'd delete the 'liberation" folder.

After *installing* or removing fonts, logging in/out or rebooting is typically required to make the change visible to the system.

Here's what the Ubuntu wiki has to sayabout fonts:  [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts).  (Perhaps a better source than random sites turned up by Google?)

---

### Post by Ko_Char on 2015-03-20
Also look here. 

~/.local/share/fonts      (The folder is hidden normally. Unhide it in File Manager. The same location as home/<your_username>/.local/share/fonts)

this command can list the fonts installed on the computer. A few fonts might not appear though.

```
fc-cache -fv
fc-list | less
```

---

### Post by Alduins_Khajiit on 2015-03-22
they are NOT in ANY of those places mentioned!!! >:( the font viewer says they ARE installed but the downloaded font manager CANNOT SEE ANY OF MY FONTS!!!

---

### Post by buzzingrobot on 2015-03-22
> **Alduins_Khajiit said:**
> they are NOT in ANY of those places mentioned!!! >:( the font viewer says they ARE installed but the downloaded font manager CANNOT SEE ANY OF MY FONTS!!!

Please paste and post the results of:

```
ls -l /usr/share/fonts

```

What is the "downloaded font manager" you are using?

---

### Post by Alduins_Khajiit on 2015-03-24
it is the font manager mentioned in the link of my OP


and the result of the code is:

shrunken-human@toilet-761GX-M754:~$ ls -l /usr/share/fonts
total 16
drwxr-xr-x  2 root root 4096 Jul 22  2014 cmap
drwxr-xr-x 21 root root 4096 Jul 22  2014 truetype
drwxr-xr-x  4 root root 4096 Jul 22  2014 type1
drwxr-xr-x  6 root root 4096 Jul 22  2014 X11
shrunken-human@toilet-761GX-M754:~$

---

### Post by buzzingrobot on 2015-03-24
If those directories contain font directories, and those font directories contain font files, then you have the standard font setup. 

Fonts can be removed, of course, by removing their folder.

"fc-match  <fontname> will tell you which font your system may be mapping to <fontname>. 

I don't use LibreOffice or other suites, but I believe they may handle their fonts independently.

---

### Post by Ko_Char on 2015-03-24
Looks like you missed the comment in your link

> Good choice! But, by default it search for  custom fonts only in ~/.fonts, instead in "Preferences" I added also  ~/.local/share/fonts, because it's the folder used by install feature of  Font Viewer. &#8211;  Pisu                 [Oct 18 '14 at 10:02]("http://askubuntu.com/questions/371213/how-to-delete-fonts-in-ubuntu#comment736682_371320") 

At the bottom left of the font manager, the 3rd icon is "set application preferences". 
You need to add a new directory there. 
Go to your <username>
Press " Ctrl + H " to show hidden files
browse to .local
share
fonts
Click OK

Set your default fonts folder to /home/<username>/.local/share/fonts

Close it and reload font-manger.

---

### Post by buzzingrobot on 2015-03-24
Admitedly, the only "font manager" I've used was KDE's a long time ago,  Didn't see that it made things any easier.

When I want to add a font, I put in into /usr/share/fonts, like so:

```
sudo cp -R <fontdir> /usr/share/fonts
sudo chmod -R +rx /usr/share/fonts/<fontdir> {just in case things are set wrong in the downlload}
fc-cache -fv
```

I seldom remove fonts, but it's just a matter of "rm -R /usr/share/fonts/<fontdir> and recaching. I have seen, once or twice, a website use a font that Ubuntu mapped to aonther font I didn't like, even though the font the site specified was on the system. Removing the font Ubuntu mapped the site's font to was a brute force way of getting the browser to display in the site's font.

---

### Post by Alduins_Khajiit on 2015-03-29
I found them

they were here: ~/.local/share/fonts

I had to hit ctrl+H in order for that to show

I removed it

I needed to remove it because it was a font that I made for my dialogues for my character art and the font name was missing the word "dialogue" in it so I had to remove the one and put another. since they had two different font titles, they would show up as two different fonts and be duplicates

---

### Post by buzzingrobot on 2015-03-29
> **Alduins_Khajiit said:**
> I found them

they were here: ~/.local/share/fonts

I had to hit ctrl+H in order for that to show


So-called "dot files" -- filenames that begin with '.' -- are a very old Unix/Linux convention intended to remove unnecessary clutter from directory listings. Other than having the dot at the beginning of the filename, they're ordinary files.  Ctrl-h in a file manager typically makes them visible.  In a terminal, 'ls -a' does the same.

---

