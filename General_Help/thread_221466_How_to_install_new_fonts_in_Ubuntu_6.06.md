---
title: "How to install new fonts in Ubuntu 6.06"
date: 2006-07-23
forum: General Help
---

### Post by leo_m on 2006-07-23
I have a TTF file for a font I want to install on Ubuntu 6.06.  While I can view the font using gnome font-viewer, I am unable to figure out a way of installing it.

I have tried to paste it to fonts:// folder but it does not get pasted (due to permissions on the fonts:// folder) and I do not know how to do it using the command line (to get around the permissions problem, by using sudo).

---

### Post by steve.horsley on 2006-07-23
I'm sure I saw somewhere that you can install fonts in Ubuntu by just dragging and dropping them to the right folder, but I don't know which folder this is. You can get a nautilus window with full privileges by entering the command **sudo nautilus**.

---

### Post by leo_m on 2006-07-23
That sudo nautilus command helped me in being able to paste the font file...thanks

---

### Post by ajgreeny on 2006-07-23
Really should be *gksudo nautilus* not *sudo nautilus*.  It doesn't often happen, but things can break if you use sudo for Gnome GUI apps.  For KDE apps it should be *kdesu* instead of *gksudo.*  *Sudo* is really for root use of terminal apps or utilities like cp (copy) or mkdir (make directory).

---

### Post by leo_m on 2006-07-23
I copied the font but the web-site which uses this font still does not render properly.

I also found out that the font gets deleted when I do sudo dpkg-reconfigure fontconfig.

Do I need to avoid the above command to use the font?  Do I need to restart the computer or carry out some additional steps besides copying the font file to the fonts:// folder using nautilus?

---

### Post by soze on 2006-07-23
You will need to
```
fc-cache
```
after copying the font file.

---

### Post by leo_m on 2006-07-25
fc-cache does not help - I ran it both as a normal user and with sudo, but the web-site does not render the font.  Also, when I close Nautilus and open it again, the font is not listed.

I searched a bit and came across a post about dfontmgr, so I installed this package, defoma was already installed.  Though this dfontmgr asked a few questions about the font I was trying to register, and I answered those questions and presumaby the font was installed/registered, yet when I go to fonts:// folder using Nautilus, I still do not find the font listed...and the web-site still does not render the font.

How to install a font in Ubuntu 6.06 then?

[update] got a step closer.  I had to copy the font file to proper subfolder under /usr/share/fonts/truetype/ folder and then register it using dfontmgr.  Now the web-site renders the font correctly, well, almost; there are some extraneous characters within words, but I can atleast make out what the web-site says...I do not know how to correct it though, will try to tweak my installation a bit and then see what happens...if I find something interesting or am able to get the font to render correctly, will update this thread.

[update] I found that I just need to copy the font file to (the appropriate sub-folder under) /usr/share/fonts/, I did not need to run the dfontmgr and the web-site is rendering the font (although not entirely correct, ie, as before (see previous update above)

---

