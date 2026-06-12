---
title: "gkismet load problem"
date: 2005-04-13
forum: General Help
---

### Post by jMack on 2005-04-13
hello-

I've installed kismet sucessfully in Hoary.  I've found another version of it called gkismet, which is GUI and not text-graphic based.

I've done the make install as they requested ([http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)) but now I get this error:
> 
root@UbuntuLaptop:~ # gkismet
Can't locate Gnome.pm in @INC (@INC contains: /usr/local/lib/gkismet /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
BEGIN failed--compilation aborted at /usr/local/lib/gkismet/GKismetApplication.pm line 27.
Compilation failed in require at /usr/local/bin/gkismet line 25.
BEGIN failed--compilation aborted at /usr/local/bin/gkismet line 25.


Anyone play with gkismet at all in Ubuntu/debian?  I can follow a how-to pretty well.  Unfortunately there's very little documentation out there on this.

kismet will work fine (got a pesky rogue Wifi in office) but looking for a better-looking one to show off to my Mac-user friend :).

---

### Post by poofyhairguy on 2005-05-06
[QUOTE=jMack]hello-

I've installed kismet sucessfully in Hoary.  I've found another version of it called gkismet, which is GUI and not text-graphic based.

I've done the make install as they requested ([http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)) but now I get this error:


Anyone play with gkismet at all in Ubuntu/debian?  I can follow a how-to pretty well.  Unfortunately there's very little documentation out there on this.

kismet will work fine (got a pesky rogue Wifi in office) but looking for a better-looking one to show off to my Mac-user friend :).[/QUOTE]


You need the 

libgnome-perl

package installed.

---

### Post by shivam.seth on 2008-04-08
yes you will need to install libgnome-perl package before installing Gkismet. 

I did the same and Gkismet did launch after that but the frontend is not working correctly for me. On launching Gkismet, a pop-up window comes up with two text fields in which I cannot type anything and just two icons. there is no text in this pop-up window. Is your Gkismet working properly after installing libgnome-perl and reinstalling gkismet? If you too have the same problem please post your reply on this forum [http://ubuntuforums.org/showthread.php?t=749102]("http://ubuntuforums.org/showthread.php?t=749102")

---

