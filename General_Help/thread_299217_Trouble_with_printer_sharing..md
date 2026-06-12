---
title: "Trouble with printer sharing."
date: 2006-11-13
forum: General Help
---

### Post by MacPC on 2006-11-13
Hi,

I am having a lot of trouble setting up my Mac to share the Ubuntu printer.

The Mac is OSX 10.4.8 and the Ubuntu is 6.06, the HP printer is connected to the Ubuntu box. Since the OSX is Unix bas, I would assume I can use CUPS on the Ubuntu box but somehow I can't get it to work. I wonder if it's something wrong with my cupsd.conf file or it's the Mac, can someone help me?

Also, where do I find out if the Ubuntu is configured to share its printer?

MacPC.

---

### Post by harty83 on 2006-11-14
I have to remember back to Dapper. In Edgy, you can open system->administration->printers.  Click on global settings and make sure share printers is checked.  This will change the conf file to listen on port 631 rather than just on 127.0.0.1:631.  

If that option is not there (I can't remember with dapper), look in /etc/cups and see if there is a ports.conf file I think it was named.  Edit that and make sure it is set to listen to port 631 rather than just from the localhost.  

I work with macs everyday but I've never set up a printer!  But you will want to set up a network printer and point it to ipp://<dapper_box_ip>:631/printers/<printer_name>.

I did read that macos sets up a wrong queue location by default and you have to change it.  Read this and see if it makes sense.

[http://ubuntuforums.org/showpost.php?p=435661&postcount=3]("http://ubuntuforums.org/showpost.php?p=435661&postcount=3")

See where that gets you if you haven't already figured it out or have tried this.

---

