---
title: "Adding TTF Fonts to Ubuntu"
date: 2016-05-03
forum: General Help
---

### Post by meetdilip on 2016-05-03
I have a pack of fonts which I would like to add to Ubuntu 14.04. It is has some 400 + fonts and I do not know how to add them to Ubuntu and make available in GIMP / Inkscape. Any help would be highly appreciated.

---

### Post by CantankRus on 2016-05-03
You can add fonts to the system by placing them in **~/.fonts**
You may have to create the directory.
Refresh font cache after adding...
```
sudo fc-cache -fv
```

I rarely use gimp but added fonts show.

---

### Post by meetdilip on 2016-05-03
Thanks for the reply @CantankRus

I do not see any **.fonts** folder under home ( I do not have any hidden files or folders ). But there is one under [I]usr > Share

[/I]When I place in usr > Share, the fonts on web page gets bold or all fonts vanish. I tried this a couple of times with the same problem. Any help ?

---

### Post by vasa1 on 2016-05-03
> **meetdilip said:**
> Thanks for the reply @CantankRus

I do not see any **.fonts** folder under home ( I do not have any hidden files or folders ). But there is one under [I]usr > Share

[/I]...
You need to _create_ *~/.fonts*!
Open a terminal and run```
mkdir ~/.fonts
```

And "I do not have any hidden files or folders" is a bit disturbing. Did you try *ls -al* or even *ls -a* in a terminal from your home folder? You should have at least *~/.config*, *~/.local*, *~/.cache*, and, if you use Firefox or Seamonkey or Thunderbird, you should also see *~/.mozilla*. 

If you're using a file manager, you should be able to **toggle** the showing of hidden files and folders using *Ctrl+H*.

PS: please update your profile information to show the version of *buntu you're currently using. I'm sure it isn't "Ubuntu 11.10 Oneiric Ocelot" :)

---

### Post by poltiser2 on 2016-05-04
It is optional to create ~/.fonts - they will show only in one user, I believe. If you put them in /usr/share/fonts they will show to every user. Command 
sudo fc-cache -fv will renew the font cache for the system to include new fonts - it works for me and I put any fonts to /usr/share/fonts including the windows fonts and it works everywhere...
;-)

Regards

---

### Post by grahammechanical on 2016-05-04
There is something else that you might try.

Copy the fonts to a folder. Open the folder in the File Manager. Select one, a few or all, the font files. Right click and select Open with Font Viewer and then click Install.

I have only ever done this with one true type font. You certainly do not want to do this one font at a time but you might want to experiment with one font and then with a few fonts. Adding 400 + in one go would keep the system busy for awhile. I should think.

Regards.

---

### Post by ajgreeny on 2016-05-04
First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```
I am using "myfonts" as an example.
Next open a terminal in the folder where you have a bunch of custom fonts and type the following
```
sudo cp *.ttf /usr/share/fonts/truetype/myfonts
```
This will copy the truetype fonts to that folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.

Now that you have the fonts in the proper folder you need to install them in Ubuntu.
Open a terminal in your newly made usr/share/fonts/truetype/myfonts folder and type the following
```
sudo fc-cache -f -v
```

This will install the fonts so that all your applications like LibreOffice, etc etc, and any other users, including the system utilities can use them.

---

### Post by meetdilip on 2016-05-04
Thank you guys. I created a* .fonts* folder in *Home* . Now I can have the fonts in Inkscape. Haven't checked yet in GIMP though.

@vasa1 

What I meant was that I have unhidden all folders which were hidden.

---

### Post by meetdilip on 2016-05-04
Update :

I have this problem since some time. Now certain websites' font has gone bold in browser after adding the new fonts. How can I fix it ?

Update 2 :

Fonts in those web pages get to normal when I delete the* .fonts* folder and restart my computer

---

