---
title: "scanning HP PSC 1510"
date: 2006-10-11
forum: General Help
---

### Post by ColinG on 2006-10-11
Having just undertaken am apt-get upgrade my scanner is not recognised by XSANE. It was ok previousely. During the upgrade I noticed a change being made to hplip and wonder if that could be the cause.

All I get is "no devices available". The actual printing side works fine.

Is this a bug or am I missing something?

Help would be appreciated.

Thanks
Colin

---

### Post by whizbaby on 2006-10-11
For my multifunction PSC1210 I installed *hpijs* and *hpoj* (the latter one is the special all-in-one psc driver). Both scanning and printing works.

---

### Post by ColinG on 2006-10-11
I've just done that, thanks, and yes now everything works fine again. I thought though that hplip was a replacement for hpoj. Could someone please comment on this?

Whizbaby, a million thanks for saving my scanning life \\:D/ 

Colin

---

### Post by fragos on 2006-10-11
I just have hplip and my PSC 1410 works fine to print and with xsane.  I also believe that hplip is a total upgrade and replacement for hpoj.  hpoj may have been for parralel port connected printers.

---

### Post by ColinG on 2006-10-12
HPOJ is for parallel and USB devices. I agree HPLIP is an upgrade but the HP PSC 1510 does not work without HPOJ being installed. That is the case in my experience anyway.

Maybe there is a bug in hplip latest version.

Thanks
Colin :)

---

### Post by ColinG on 2006-10-17
O've just done an update after being way from my box for a few days. I noticed hplip was updates again so I uninstalled hpoj to see what would happen. My 1510 now works with hplip alone hpoj is not needed :D

---

### Post by ilbozo on 2006-10-17
I have the same printer (1510 PSC) and i just installed latest HP drivers (1.6.10) instead of the drivers that i got in edgy repos (1.6.9). The old drivers were working well but i wanted the useful panel of hplip that i saw on Mandriva One. I dunno if it was the best way to obtain that but it worked.
Now i have the "HP Device Manager" in menu Accessories that manages everything of the printer (Print, Scan, Fax etc). 
I'm going now to write a "guide" if someone would try that...

---

### Post by ColinG on 2006-10-17
How did you go about actually installing the new version. I'm a bit of a noob when it comes to installimg outside Synaptic:( 

Thanks
Colin

---

### Post by ilbozo on 2006-10-17
It's quite simple.
Just download [this file]("http://prdownloads.sourceforge.net/hplip/hplip-1.6.10.run").
Make it executable 
```
chmod +x hplip-1.6.10.run
```

Then install required packages running in terminal:
```
sudo apt-get install build-essential libjpeg62-dev python-dev libcupsys2-dev libusb-dev lsb openssl libsnmp9-dev python-qt3 python-reportlab sane-utils
```

Maybe could appear a Postfix configuration wizard. I choose to not configure at this time postfix. I think it's related to the fax function of the sw.

Then run the script simply doubleclicking it! 
It will ask you few question:
The first is for the automatic installation (choose "a" if you don't want to set single functions)
The others are questions about your system. Choose obviously Ubuntu and then your version.

Finally will start the tool for configuring your printer. in graphical mode.

---

### Post by ColinG on 2006-10-17
Excellent stuff.

many thanks
Colin:)

---

### Post by StanMeis on 2006-12-26
Thank you ilbozo for the excellent tutorial.  If a rookie like me can have complete scanner/printer functionality within minutes by following your directions anybody can.

---

