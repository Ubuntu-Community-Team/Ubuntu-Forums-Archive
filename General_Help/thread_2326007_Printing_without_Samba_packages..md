---
title: "Printing without Samba packages."
date: 2016-05-27
forum: General Help
---

### Post by oceola2 on 2016-05-27
It's a simple question apparently without any simple answers.
Is it possible to remove all vestiges of Samba, clients and related libraries and data files and still have printing?
I seem to remember rem9oving samba and it's related files on earlier version of Ubuntu but now I get a long dependency list of files to be removed.
Before, if memory serves there was the ability to remove samba along which removed the system config print packages but a re-install allowed for their re-install without the samba packages. I could be wrong on this but I'm wondering if it is needed on a system without any MS detritus?

Thanks

---

### Post by ajgreeny on 2016-05-27
Why do you want to remove samba?  If you don't actually use it to share with a Windows OS (or another Linux system which it will also accomplish) it simply uses a little bit of space, but importantly, no resources.

See [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba) for a lot of info about samba.

---

### Post by gsahli on 2016-05-27
Although you can print with samba, it isn't the print control system, and isn't at all necessary for printing. CUPS (common unix Print System) is the print system on nearly all linux systems (and Mac OS X).
You can remove samba (I don't know if it's possible) and still print.

Maybe you should describe what you want to do.

---

### Post by oceola2 on 2016-05-28
What concerned me is couple of updates ago of samba and samba libraries I believe it was responsible for causing problems with my printer.
Though I have a currently available HP printer, LaserJetPro 400 M401n (wired printer, not wireless), I have to resort to alternative packages instead of the normal HP packages.
I believe some reference which doesn't show this printer inside of the those Samba updates blocked the printer use.
I removed the main package and re-installed the printer and so far so good but I seem to remember this occurring with an earlier printer several years ago and the solution was to dump most of the HP packages but it was necessary to dump Samba as well.
I could be completely wrong ijn this but if it's not necessary why all the dependencies shown in Synaptic.
Am I correct Samba is a MS originated package and unnecessary unless sharing the printer with other networks or sharing other network printers.
It's also a slight security concern as I see all sorts of unsecured printers when I turn on the wireless and even though there's no wireless driver installed is the possibility of the "share" concept sending that printed file to those unsecured wireless printers.
Could be just another case of tinfoil origmai. :)

---

### Post by Morbius1 on 2016-05-28
Samba - the package - is not a Microsoft originated package. It was a UNIX originated package created originally so UNIX could provide file and printer services to Windows clients. A lot has happened since it's beginnings however so now Apple's OSX for example has their own in-house designed version of Samba - both server and client  components - which is set as the default file sharing mechanism.

Samba - the package - is the Samba server component as in not installed by default in Ubuntu. Smbclient ( the client component of samba ) is installed by default in 14.04 but only libsmbclient is installed after that.

The reason you automatically see various printers on your network is most likely due to cups-browsed:

> This package provides cups-browsed, a daemon which browses the Bonjour
broadcasts of shared remote CUPS printers and makes the printers
available locally, replacing the CUPS broadcasting/browsing which was
dropped in CUPS 1.6.x. This way the old behavior of having the remote
printers available automatically is now re-implemented with Bonjour.
Apple created Bonjour and in Linux it's called Avahi. In fact Apple created CUPS ( actually they hired the guy that created it ):
> CUPS is the standards-based, open source printing system developed by [Apple Inc.]("http://www.apple.com/") for OS X[SUP]®[/SUP] and other UNIX[SUP]®[/SUP]-like operating systems. CUPS uses the Internet Printing Protocol (IPP) to support printing to local and network printers.
So the moral of this story is that all operating systems "borrow" from each other.

Card carrying members of the Penguinista Liberation Front based on something they once heard from a friend of a friend who knew a guy that said that samba is just for Windows attempt to pugre themselves of all things Samba. It is unknown if they know about the Apple tie in to CUPS or they would likely try to purge themselves of that as well.

---

### Post by gsahli on 2016-05-28
If by "wired" you mean it is an ethernet-connected network printer, I don't see any connection to samba. Samba "can be" the connection protocol for printing through CUPS, but you have to select that intentionally for it to be used. Morbius1 has explained the avahi/bonjour CUPS browsing things you're likely seeing.
Use the HP Jetdirect-socket protocol to print to that printer. It's the most reliable one for HPs anyhow.

---

### Post by oceola2 on 2016-05-30
@Morbius1 - Thanks for the clarification on Samba origin. The printers show up in the wifi networks panel and there's no indication of them in Network connections. It's just the folks who own them apparently haven't made them secure. I realized the fault with cups-browsed a few Ubuntu versions ago and have removed or disabled it with each version update.

@gshali - by wired I mean the printer is hooked up with a cable to the computer and has supposed to have no wireless capability. The main reason I bought it. My concern which again is probably a bad fold in my tin foil is when I print is there some pickup by unsecured wireless printers which show in the wifi list of other wifi connections, some of which are the unsecured printers, of anything I print. Jet direct is removed and am operating on generic drivers under foomatic. Due to the missing printer drivers in the updated HP packages I am working off an older HP package which I've archived which also supports an older HP 3400 scanner.

---

### Post by gsahli on 2016-05-30
Unless you select some other printer to print to, there is no way that print data is going somewhere else.

FYI, the useful description would be "USB-connected printer."

---

### Post by oceola2 on 2016-06-01
@gsahli - Thanks for the reassurance on the printing and you're right on the USB since parallel has gone the way of the Dodo. ;)

---

