---
title: "Installing fonts"
date: 2022-04-06
forum: General Help
---

### Post by Donnie Love on 2022-04-06
I need to know how to install fonts on Lubuntu 21.10

---

### Post by &amp;KyT$0P# on 2022-04-06
Is it enough to just copy the font file to [FONT=Courier New]~/.local/share/fonts[/FONT] (create this folder if it does not exist)?

---

### Post by Donnie Love on 2022-04-06
> **halogen2 said:**
> Is it enough to just copy the font file to [FONT=Courier New]~/.local/share/fonts[/FONT] (create this folder if it does not exist)?

Permission denied.

---

### Post by &amp;KyT$0P# on 2022-04-06
I take it the folder exists and that is the error you get when attempting to copy the font file there.

Please post the output from running this command in Terminal -
```
ls -la ~/.local/share/fonts
```

---

### Post by GhX6GZMB on 2022-04-06
Double, sorry.

---

### Post by GhX6GZMB on 2022-04-06
I've never found a good way. You can install single fonts using Muon, but that's a nightmare.
The so-called "Font Manager" is complete manure.

I resorted to installing the fonts manually by simply copying them (in my case from Windows). This breaks the connection to Synaptic and Font Manager, but who cares?

Here's the recipe:

[I]**Fonts (check your installed fonts before proceeding!!)**

A standard installation will have around 100 installed as default, all of them show Western and many also have Asian typefaces.
Adding or removing fonts using Font Manager is a Sisyphos job, I prefer installing or removing fonts directly. This will ruin the font synchronisation with the installed packages database, but that&#8217;s not big issue. You don&#8217;t really need it.

Open the PCManFM-Qt File Manager as a root session (&#8222;Tool&#8220; - &#8222;Open as root&#8220;) and go to:

    /usr/share/fonts/truetype

Delete the font directories/files you don&#8217;t want to keep.
For installing new fonts from somewhere else, simply copy the new font directories/files to the  /usr/share/fonts/truetype directory. Each font should have its own directory with the actual font files stored within.

The new font directories and files need correct ownership and user access permissions. Generally, fonts belong to the operating system and need owner root, group root. The user permissions must be be 755 for the font directories and 644 for the font files.
Run these commands to set them:

    sudo chown -R root:root /usr/share/fonts/truetype
    sudo chmod -R 755 /usr/share/fonts/truetype
    sudo chmod 644 /usr/share/fonts/truetype/*/*

Finally, make the fonts accessible to all by running:

    sudo fc-cache -f -v

Done. Your new font set is now available to all programs.[/I]

---

### Post by Donnie Love on 2022-04-06
ls: cannot access '/home/donnie/.local/share/fonts': No such file or directory

---

### Post by Donnie Love on 2022-04-06
I got it now. Thank you.

---

### Post by &amp;KyT$0P# on 2022-04-06
If you open [FONT=Courier New]/home/donnie/.local/share[/FONT] in PCManFM, can you create a folder there named "fonts"?  If so, try that and copying your font there?  If not, please post the output from running this command in Terminal -
```
ls -la ~/.local/share
```

ml9104's method for installing/removing fonts is for doing it system-wide, which I would think is only needed if you have multiple user accounts on your computer and want to install this font for all.  Otherwise the home directory based method is simpler if it works in Lubuntu.

* Oops, posted at same time as your last post.  Thanks for reporting back.

---

### Post by GhX6GZMB on 2022-04-06
> **halogen2 said:**
> 
ml9104's method for installing/removing fonts is for doing it system-wide, which I would think is only needed if you have multiple user accounts on your computer and want to install this font for all.
Correct. I have the belief that fonts belong to the OS, and yes, my machines have several user accounts.
But the installation in $HOME is also fine. The important thing is running *fc-cache* at the end.

---

