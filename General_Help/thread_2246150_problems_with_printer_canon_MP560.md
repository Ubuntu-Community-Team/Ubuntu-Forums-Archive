---
title: "problems with printer canon MP560"
date: 2014-09-28
forum: General Help
---

### Post by drdob on 2014-09-28
Dear all  having left Ubuntu I am now back. Sorry, can you help me I have a canon MP560 printer can I get it to work no...  I have tried the help forum and tried the work rounds but still no go. Has anybody any idea.  thank you Michael

---

### Post by pdc on 2014-09-29
so Canon supply a 32bit driver 

you can get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html?r=s&q=) and it comes down as cnijfilter-mp560series-3.20-1-i386-deb.tar.gz

and before install, you need libtiff4 from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go about 14 down the list to find libtiff 4

_____________

commands in a terminal to install the printer driver are:

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mp560series-3.20-1-i386-deb.tar.gz
cd cnijfilter-mp560series-3.20-1-i386-deb
./install.sh[/COLOR]

---

### Post by drdob on 2014-09-29
PCD thankyou for your reply, i have tried this and it does not work. :( i get a note "Broken dependency " with the deb file from canon and the Lbitff is 'old' and i have a newer one installed. i can see my printer on the wifi but i need the bessed driver.. yours Michael

---

### Post by pdc on 2014-09-29
are you using 32bit? are you running 9.04 ubuntu?

---

### Post by drdob on 2014-09-29
hi PDC i am running 14.0 67 bit thanks for taking the trouble Michael

---

### Post by drdob on 2014-09-29
well thankyou all of you on the forum, both past and present, and thank you pdc i'v done it i followed the above and used the packet manager and it works!! :popcorn:
please do not ask me how, :confused: but i did it. yours Michael

---

### Post by pdc on 2014-09-29
well done; you're a genius Michael !! enjoy!!

as you initiated the thread, you can use Thread Tools at the top of the menu to add [COLOR="#0000FF"]SOLVED[/COLOR] to the title of the thread ..............

---

