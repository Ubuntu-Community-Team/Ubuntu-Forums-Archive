---
title: "How to input pinyin accents"
date: 2013-10-02
forum: General Help
---

### Post by James Wilde on 2013-10-02
Hi:

I have installed iBus and several pinyin input methods for Chinese characters.  What I would like to find is a system for writing pinyin showing the accents.  On the Mac one can input Alt+u, Alt+e, Alt+i or Alt+' followed by the vowel to be accented, and the accent will show.  I think there is something similar for Windows.  Is there an equivalent for linux?

My system is running 13-04 64 bit

Grateful for any help.

//James

---

### Post by James Wilde on 2013-10-03
Ok I have a Swedish keyboard and can input the grave and acute accents from a special key.  The other two accents are called caron and something else.  One of them is a straight horizontal line over the vowel, the other is a v-shaped accent over the vowel.  Another of my dead keys on this keyboard contains the circumflex as in French: â and that funny curved line they use in Spanish: ñ.  I don't use these two symbols so I'll try for a key change to the two accents I need.  If it works, I'll change the thread to solved.  More tomorrow.

---

### Post by James Wilde on 2013-10-05
Fixed it!  I used xmodmap.  Find a key on your keyboard that you can do without.  In my case it was a key two to the right of the 'p' key, which has diaeresis (two dots over a vowel) as the base symbol, circumflex (an upside down v) in the shift mode, and tilde (the squiggly line over some 'n's in Spanish) with AltGr.  I wanted to change this to produce the caron (a v-like symbol as in &#462;) in the shift mode, and a macron (a flat line as in &#257;) with AltGr.  The diaeresis could stay as I sometimes use it.

I executed the following commands:

xmodmap -pke > .Xmodmap.org  this saves a copy of your original keyboard mapping -  Note, save all files in your home directory.
xmodmap -pke > .Xmodmap  or you can just cp .Xmodmap.org to .Xmodmap
vi .Xmodmap

With this command you can edit the file with the new keymaps.  I changed dead_circumflex to dead_caron on key 35 and dead_tilde to dead_macron on the same key, of course.

Now, with the command

xmodmap .Xmodmap

you load the new mapping.  To make this permanent (so it doesn't revert on reboot) you must enter the line

xmodmap .Xmodmap 

in a file called .xinitrc in your home directory

Bingo.

---

