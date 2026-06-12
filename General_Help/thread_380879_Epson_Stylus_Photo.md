---
title: "Epson Stylus Photo"
date: 2007-03-10
forum: General Help
---

### Post by Dale Gerdemann on 2007-03-10
I got a new Epson Stylus Photo RX640. Somewhere on the web, I got the info that the RX series was good under Linux, but it seems not to be true. I checked out this site:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX640](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX640)

and I see a lot of talk about half-baked solutions. 

I also checked turboprint, and didn't find my model there either.

I'm thinking I might just wait, and use my dual-boot system to print under XP for a while, until a solution comes along. But I'm not sure how realistic this is. Can I reasonably expect an improvement to come along? Or is there something I can do now to get this thing working?

Thanks,

Dale Gerdemann

---

### Post by compmodder26 on 2007-03-10
I have an RX620 and it works near perfectly.  The only thing that doesn't work is borderless prints but I just copy the pictures I want to print onto a memory card and print directly from the printer to get around that.  Of course, I don't think they make the RX620 anymore.

---

### Post by Dale Gerdemann on 2007-03-11
compmodder26  wrote:

... I just copy the pictures I want to print onto a memory card and print directly from the printer ...

Interesting! How does this work? Do I need some special hardware to print onto a memory card?

---

### Post by compmodder26 on 2007-03-12
Here is what I do:

1. Copy the pictures I want to edit off of my digital camera and into ubuntu.
2. I edit my pictures (remove red eye, crop, etc.) in Gimp and save them.
3. Re-copy the pictures back onto my digital camera.
4. Plug my camera into my printer and then use the printer interface to print the photos.

---

### Post by jibe74 on 2007-03-23
Hi,

Thanks, [compmodder26]("http://ubuntuforums.org/member.php?u=15583") ! This can be an interesting work around for the photos. 

But did somebody found a solution, at least for simple printings ? Is there another (almost) compatible driver ?

As [Dale Gerdemann]("http://ubuntuforums.org/member.php?u=181926"), I'm surprised to experience problems installing this printer, as usually Epson has good drivers for Linux... I'm looking for a solution, but seems that Google knows more about problems than solutions about this printer :(

---

### Post by cotcot on 2007-09-30
In case you are still searching :

I have compiled gutenprint-5.1.3 (downloded from their website) using the normal way (./configure, make clean, make, sudo make install)
Then I manually made the directory /usr/share/cups/model/gutenprint/5.1.
Then I ran the command 

```
sudo cups-genppd.5.1
```
 and configured the printer with cups ([http://localhost:631/](http://localhost:631/)).
Printer works fine on my 7.04 64bit system (it worked on the 32 bit as well)

---

