---
title: "server or desktop edition?"
date: 2007-03-22
forum: General Help
---

### Post by wwuster on 2007-03-22
I need to replace a FreeBSD server with Ubuntu. I know that I could install the server edition. But I'd also like to have a graphical desktop. I've setup a few desktop editions with apache2, mysql, and php and use them as servers. That wasn't a big deal. I guess that you could also install gnome on a server edition. Does it matter which edition I install for use as a server with occasional web browsing? I'm leaning toward just installing the desktop edition and add the server things that I need. Is there a reason not to do that?

thanks,
William

---

### Post by arbulus on 2007-03-22
It might also depend on if you plan on using a software RAID on your server.  If so, then you should use the Alternate Install disc, since the Server and Desktop editions don't allow for software RAID installations.  I installed it on a 3 HDD RAID 0 on a server I use for file and print sharing, and it went very well.  It installs Gnome by default.  Otherwise, I don't see why you couldn't use the desktop edition, and then just customize the install for the packages you do or don't want.  The Server Edition makes it easy to set up a LAMP server right at the installation, but it's not at all difficult to install those apps in the Desktop Edition after installation.

---

### Post by louieb on 2007-03-22
Don't know the specifics but the server kernel is tuned differently from the desktop kernel. In the end I don't think you will notice much if any difference. I've gone the desktop route and added LAMP server stuff to it. Had to do a little tweaking to get it going. The LAMP server install ran out of the box. Have not added a desktop to it.

---

### Post by indytim on 2007-03-22
I can't believe you haven't gotten a response on your posting yet. :roll: 

If you want to go light weight with a lower load on resources, you could do Xubuntu and build your LAMP server from there.  Or do the server build and add Xubuntu later.

I've got a full blown Kubuntu running with a LAMP server.  I need the full GUI from Kubuntu and the LAMP is used for development only.

There are lots of other options out there.  Hopefully, you'll get additional responses from the collective.

IndyTim

---

### Post by MaLk0 on 2007-03-22
I have an old laptop running as a fileserver and media server. I am running with Ubuntu 6.06 desktop install and it works like a charm. If it is just for home use I do not think you will notice any difference between server and desktop edition.

---

### Post by wwuster on 2007-03-22
The other desktop-edition machines that I use as servers are on my personal lan. The one I need to install next is open to the public and not on my LAN. It seems that performance might be an issue with the desktop-edition. Has anyone put gnome on the server edition?

thanks,
William

---

### Post by mcduck on 2007-03-22
> **wwuster said:**
> The other desktop-edition machines that I use as servers are on my personal lan. The one I need to install next is open to the public and not on my LAN. It seems that performance might be an issue with the desktop-edition. Has anyone put gnome on the server edition?

thanks,
William

It makes no difference if you run desktop on desktop version or server version, you'll be running exactly same desktop in either case ;) (unless you use the server version and then add only those desktop packages you need one-by-one, but I don't think you'd notice any real difference even that way)

---

### Post by JoxBG on 2007-03-23
Install the Server edition, it's so much lighter at startup on resources which then gets used for real work by the server. For graphical login to ease your sysadmin job, grab either IceWM or FluxBox (or both) as window manager and GDM as login manager though I'd recommend a lighter one, WDM. Get Rox-filer for file management and sometimes desktop (using the pinboard option), sylpheed-claws for reading mail. You can use firefox for web browsing, but for fast text browsing, dillo is the way to go. The best part of server install, you get to choose what packages to add, all at the convenience of a simple command.

---

### Post by AndyCooll on 2007-03-23
Install the Server edition. You can always manually add a desktop environment (whichever one you prefer) following this.

:cool:

---

