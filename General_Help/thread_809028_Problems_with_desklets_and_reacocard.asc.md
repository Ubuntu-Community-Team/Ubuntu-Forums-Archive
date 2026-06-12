---
title: "Problems with desklets and reacocard.asc"
date: 2008-05-27
forum: General Help
---

### Post by Kofaggare on 2008-05-27
It's time to make my ubuntu 8.04 desktop practical and beautiful.

At first I had problems with Avant Window Navigator. After following instructions everything went fine until:
> 
 wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
--09:16:30--  [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
           => `reacocard.asc'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:16:30 ERROR 404: Not Found.

So it seems that tuxfamily has removed reacocard once and for all or behind some other url (which I couldn't find). Can anyone help with this problem?

-Unfortunately problems haven't yet ended.

So the second problem is with gDesklets and aDesklets which both ones outputs error after trying install a new desklet. Maybe an example desklet would help advising, so here it comes:


[Here is the description of the desklet]("http://www.gnome-look.org/content/show.php/lukas+desk_op-let?content=71314")

[And here direct link to desktoplets .tar.gz folder]("http://http://www.gnome-look.org/CONTENT/content-files/71314-lukas_deskoplet-6.tar.gz")

After trying to install above-named desklet with gDesklets "Install remote package"-feature the only output is 
> 
"The package could not be installed because it contained no installable files." 

which sounds little bit strange to me because i tried that with many kind of desklets and always the program outputs the same message.

I won't quit after first try so I tried to solve the problem this way: I extracted the content of package to my home folder manually and tried to bring that desklet with "Install package"-feature. After ordering gDesklets to open lukas' "desk.sh"-file appears a window that says:
> 
 "The supplied file could not be opened as a package. It is either corrupted or not of the correct file type." (and yes I've tried .py and other kind of formats with various desklets)

If graphical way doesn't work we'll have to try to solve the problem with terminal. (In that order 'cause I'm only a beginner :)) So I installed aDesklets following the instructions and tried to open file. Only thing that I reached with that try were error kind of this: 
> 
python: can't open file './cpu_meter.py': [Errno 2] No such file or directory
python: can't open file './mem_meter.py': [Errno 2] No such file or directory

So thank to people who had enough interest to read this whole thing and specially to those who even tries to help. Beautiful and easy-to-use desktop could help new ubuntu-user like me to accustom the new OS and finally grow up from windows roots. :>

---

### Post by moonbeam on 2008-05-27
reacocard started using a PPA repository a while ago.

See [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) for the updated info.

---

