---
title: "Canon MX320 printer on Trusy"
date: 2014-07-18
forum: General Help
---

### Post by ventrical on 2014-07-18
I had one of my most embarrassing PC moments yesterday doing a migration of Ubuntu Trusty for a client and then the Canaon MX 320 printer would not work properly.  I did a search and found a web site:

[http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/)

that proclaimed it could help.

Before I try this are there any other ideas that anybody has which I could try that may solve the problem.

 The printer will begin to print a test page.. then halt .. slow right down .. pause and then after a while will finish printing. After this , trying a standard print job will fail.

Regards and thanks in advance.

---

### Post by pdc on 2014-07-19
so one could just get the 320 driver from Canon [http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html) but way back then; 2009; they only issued a 32bit debian package; 

.........and I don't know if the michael gruz repository offers more than that; 

ubuntu seems to have left libtiff4 behind; so the Canon drivers seem to need that added; the link you gives the good detail on doing that; one can also source it from the pure springs of the Debian repositories [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)

___________

if you have done a 64bit install, you will likely need symbolic links won't you to get the 32bit driver to work?

______________

the gutenprint project [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php) seem to feel the gutenprint will drive the MX320 as an alternative

---

### Post by ventrical on 2014-07-19
Ok... thanks for those links. More study for me.  I tired the process from the original link I posted for a Canon MP520 and it brought that derelict back into commission.  Also for the one in question, but there is still the stalling - but the print jobs do finish. Since the days of the start of Saucy Salamander , installing printers drivers seems a little more complex but I must admit it has not been my personal forte'. Scaling has also been an issue but I finally figured it out.

  Some Ubuntu migrations deal with tough 'super-customers' and when a printer hicups it sort of takes the gloss off of the pitch.

Thanks and regards,

Ventrical

---

