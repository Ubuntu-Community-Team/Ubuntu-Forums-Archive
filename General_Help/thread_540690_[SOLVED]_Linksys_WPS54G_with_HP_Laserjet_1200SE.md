---
title: "[SOLVED] Linksys WPS54G with HP Laserjet 1200SE"
date: 2007-09-01
forum: General Help
---

### Post by Siph0n on 2007-09-01
I am confused about printing in linux... do i HAVE to have cups? are there files I can edit, instead of using the System->Admin->Printing tool? If I choose windows network printer (SMB) in the Printing tool, do I have to set up Samba also?

I have a HP Laserjet 1200SE attached to a Linksys WPS54G wireless print server. I have used the Printing tool found in System->Administrator and made a new printer. I found the HP Laserjet 1200, and chose pxlmono (also tried Postscript) as the driver. I choose network printer for the printer type and than Windows printer (SMB). I tried putting in the information I found from a test page i printed out from a windows computer on my network, but had no luck. Any help would be awesome... I downloaded the Postscript drivers, and tryed to click Install Driver and chose the file, but now I have 3 Postscript drivers listed... Is there any way to delete them? I never touched Cups or Samba, so maybe that is the problem?

Shawn

---

### Post by geraldm on 2007-09-01
It is not necessary to use cups to print.  I have my printer setup to print directly out of
ghostscript-8.60.  Perhaps you can adapt your setup.  I detail my setup here.

I have a Samsung ML1210 laser 600dpi printer - a "winprinter"
I do not use cups or other printing daemons.  The printer is set up with a centronics-type
printer cable (I am not using USB for this).  I use scripts to view the postscript source,
and also to do the printing.  The program I use is ghostscript-8.60.
I currently have only the 1 printer hooked to the computer, and it is /dev/lp0
The environment variable GS_FONTPATH must contain the path to the fonts

To print the postscript file I use this script called printgdi
/code:
#!/usr/bin/env bash
# Author.       Gerald Murray
# Useage: printgdi filename.ps
# ghostscript-8.54 requires that environment variables be set
GS_FONTPATH="/usr/share/fonts/type1/gsfonts" 

# test for font directory
[ ! -d $GS_FONTPATH ] && echo "FATAL: $GS_FONTPATH not found" && exit 1;

if [ ! $1 ] 
then
        echo "Usage: $0 filename"
        exit 1;
fi
if [ ! -f $1 ] 
then
        echo "file $1 not found."
        exit 1;
fi

gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE \
        -sDEVICE=gdi  -sOutputFile=/dev/lp0     $1 

/code

To view the file without printing, change the "-sDEVICE=gdi" to "-sDEVICE=x11"

good luck,
Gerald

---

### Post by pete83 on 2007-09-03
Hi, I found setting up the WPS54G a little tricky. If that is your difficulty too, see my thread at:
[http://ubuntuforums.org/showthread.php?t=516747]("http://ubuntuforums.org/showthread.php?t=516747")
The key, I think, is to add a netwrok printer of IPP type, and then enter an address similar to this:
> ipp://192.168.1.44:631/ipp/P1
... but of course, use whatever the appropriate ip address is for you.

---

### Post by Siph0n on 2007-09-04
Thanks, it works now!!! I used network printer and the ipp address for the printer and it works perfectly! :)

Shawn

---

