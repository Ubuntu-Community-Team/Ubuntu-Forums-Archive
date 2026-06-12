---
title: "Sending FAX under Linux"
date: 2005-04-28
forum: General Help
---

### Post by K_Dallas on 2005-04-28
Hi!

I have never been able to use my modem under Linux and since my Windows has always been sitting there I used that for such purposes.

Now, after buying a hardware modem which seems to be recognized by wvdial, I am tempted to send faxes right from my linux box but I have no clue as how to do it.

Under Windows, it is usually a printer driver which takes care of sending faxes, how does it work under Linux?

Thanks in advance for any help.

K_Dallas

---

### Post by az on 2005-04-28
You can use efax-gtk.  I think it is in universe.

It can send and receive.  I have only ever sent faxes that were saved postscript files on hy harddrive...

---

### Post by K_Dallas on 2005-04-29
Thanks azz, I am going to try it today.

K_Dallas

---

### Post by moon2js on 2005-05-03
[QUOTE=K_Dallas]Thanks azz, I am going to try it today.

K_Dallas[/QUOTE]

Let us know how it goes, I tried to get efax to work a couple months ago as a newb, but couldn't get it to work properly.

---

### Post by zero0w on 2005-11-17
I have tried efax-gtk, and it works great.

The only problem I have found is the space for the sender information (Name and Number in the setting menu) is too small and the receiver may find it difficult to read about them.

---

### Post by garciadc on 2005-11-23
zeroOw (or anybody else with knowledge),
     I was wondering if you could tell us what you did, what modem you have, etc. bc I am trying to send a fax, and I am not getting anywhere. I have Intel 537 [AC97 Modem] on my laptop (2.6.12-10-amd64-k8), and I can't figure out how to convert tiff or txt to tiffg3.  I know that I'm not typing command correctly in terminal using efix.  Did you send a fax in a similar fashion?  Please help.  Thanks

---

### Post by patrick295767 on 2006-03-01
Hi

I tried :
```
efix -i tiffraw zessai.tif -o tiffg3 zessai-fax.tif
```
and not workign either 

:confused: :-k

---

