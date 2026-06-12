---
title: "Wine help"
date: 2005-04-23
forum: General Help
---

### Post by Nez7165 on 2005-04-23
when running winetools it gets to a point then crashes,

Parameters are Invoking /usr/lib/wine/wine.bin winepath.exe -l --new ...
winepath: invalid option L"--new"
Try 'winepath --help' for help
Choice is Create a fake Windows drive with checked=F
waiting for wineservers to exit...


thats the error any ideas on wat to do thanks

---

### Post by bin on 2005-04-24
I've always used winesetuptk with good results

Make sure you've already installed wine, wineutils and libwine via apt-get or synaptic, install winesetuptk and then just open a terminal and type wine - no sudo required. It will then launch a simple setup process. As a matter of course I always set the fake windows as /home/user_account/c - that way you can always see it as opposed to the hidden folder most setup utils want.

Thinking about it I'd suggest you make sure any .wine or fake windows files have been removed before you start again.

bin

---

### Post by crazybill on 2005-04-24
Maybe you can't put new Wine into an old box (Sorry!)

---

### Post by az on 2005-04-24
winesetuptk is depreciated.  Use the ubuntu packages from winehq.  They break every now and then and as you would have it, the versions in Hoary Universe do not work well. 
Winetools is the way to go.

---

