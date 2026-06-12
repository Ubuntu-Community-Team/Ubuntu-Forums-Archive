---
title: "[SOLVED] UPS settting up software"
date: 2007-07-04
forum: General Help
---

### Post by Gabn on 2007-07-04
I just purchased a generic generic UPS. 660Va  [http://www.fentonups.com/Products/PowerPal/powerpal.html](http://www.fentonups.com/Products/PowerPal/powerpal.html)

I did a quick search and someone else brought a ups which uses the same software as mine does 
[http://ubuntuforums.org/showthread.php?t=291069](http://ubuntuforums.org/showthread.php?t=291069)
it uses UPSilon 2000 to control the ups, it's made by a company called [http://www.megatec.com.tw/](http://www.megatec.com.tw/)

how do i know if one the computer has detected the ups on the serial port ? 

If i actually need to install there very buggy looking software ? 

What are other alternatives to the  offical software which might work. 

they actually have released some simple data could i write my own program ? (no idea how to interface with serial ports) 
[http://www.fentonups.com/Support___Service/Cables___Comm_Info/cables___comm_info.html](http://www.fentonups.com/Support___Service/Cables___Comm_Info/cables___comm_info.html)

---

### Post by francf on 2007-07-04
Try apcupsd.

---

### Post by Gabn on 2007-07-07
I fixed this problem by installing NUT [1] and it seems that the Fenton PowerPal helped the nut project and donated a UPS [2] if you have come across this looking for other UPS programs check out the compatibility list [3]

and following the guide here. 
[http://www.engadget.com/2006/07/25/how-to-network-your-ups/](http://www.engadget.com/2006/07/25/how-to-network-your-ups/)

[1] [http://www.networkupstools.org/](http://www.networkupstools.org/)
[2] [http://www.networkupstools.org/acknowledgements.html](http://www.networkupstools.org/acknowledgements.html)
[3] [http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html)

Once you have nut installed an running fine for those non-system administrators there is gui front end knutclient for all your GUI goodness (notice you have to get all the backend stuff working before knutclient works)
[http://www.knut.noveradsl.cz/knutclient/](http://www.knut.noveradsl.cz/knutclient/)

there is also a Knutsettings program which means you can avoid the terminal totally but i didn't use it and it also isn't in the repositories [http://www.knut.noveradsl.cz/knutsetting/index.html](http://www.knut.noveradsl.cz/knutsetting/index.html)

---

