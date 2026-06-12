---
title: "Default paper size problem when printing"
date: 2007-04-15
forum: General Help
---

### Post by feradz on 2007-04-15
Hi,

My printer always prints Letter format instead of A4.

After I installed Edgy, I experience very frustrating problem with my printer when I print **PDF** and **PS** files. When I print a PDF or PS the printer (Laser Jet HP3390) gives a warning message that there is no loaded Letter format. When I agree to continue printing it prints in Letter format.

I read a lot of staff about configuring and setting up a CUPS printer but ultimately I couldn't figure out how to fix this problem. I suppose this is a bug.

Besides I did all the recommended things in all available forums an mail lists:
1. /etc/papersize is A4
2. I updated the /usr/share/gs-esp/8.15/lib/gs_init.ps to be A4
3. My printer settings are A4
4. My regional settings are Spain (where the default paper size is A4)

Notes about my configuration:
1. Printer: Laser Jet HP3390
2. Network printer
3. Use hpijs instead of recommended postscript (although I tried it with the postscript)

I would highly appreciate your comments and suggestions about to fix this printer problem. 

Thanks,
Ferad Zyulkyarov

---

### Post by llamakc on 2007-04-15
Have you restarted CUPS after editing /etc/papersize ?

**sudo /etc/init.d/cupsd restart**

---

### Post by feradz on 2007-04-15
Yes I restarted the cupsd. Even restarted the computer. I think it is more related with ghostscript because when I print to a PS file it is also in letter format.

---

### Post by blindfish on 2008-01-06
I do have the same problem with Ubuntu 6.06 LTS 2.6.15-29-amd64-generic and an old HP LaserJet IIp series on lpt1:

- the printer requires letter when printing from Evince although print options are set to A4
- the printer requires letter when printing from Firefox (print options and about:config are set to A4)
- Openoffice prints on A4.
- test pages are printed on A4

What I tried/checked already:
- /etc/papersize contains A4
- the ppd file contains A4 as the default
- /etc/environment contains LC_PAPER=en_GB.UTF-8
- the option of the Gnome printer administration is set to A4
- the option of the CUPS adminstration (localhost:631) is set to A4
- I deleted and re-installed the printer several times (with and without restarts of the PC)

Without being able to print properly Ubuntu is worthless for me. Do you have any ideas what else I could try?

---

### Post by schallstrom on 2008-01-08
I have pretty much the same problem with Ubuntu 7.10 and a HP Laserjet 4000 :(

Ubuntu always wants to print in letter format but my printer uses and expects A4. All Cups settings I found are set to A4 as well as /etc/papersize.

However, some of my env vars are set to US because I prefer using an English system rather than German:
```

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

```
Maybe it has to do something with it, which would be pretty stupid. I want to be able to configure my paper size independently from the system language.

---

### Post by blindfish on 2008-01-17
After searching for a long time I finally found the cause of my problem. For a reason I don't understand, Ghostscript insists on formatting everything to letter format, no matter what the settings are. Printing test pages or from Openoffice doesn't involve Ghostview. That's the reason why the wrong behaviour doesn't occure there. Probably the papersize parameter is not given correctly to Ghostscript and it therefore uses its own default value, Unfortunately I'm too dumb to get this fixed at the right place. But the following hack worked for me:

The settings for Ghostscript can be found in the file /usr/share/gs-esp/8.15/lib/gs_init.ps (on my system). In this file I removed the percent character at the beginning of the line "% /DEFAULTPAPERSIZE (a4) def". The section reads now:

```

% Optionally choose a default paper size other than U.S. letter.
% The default page size for many devices is set at compile time to
% letter, but this can be changed to A4 although this is rarely done. 
% Some devices such as bbox have a different default page size,
% and should not be set to A4 or letter.
% When ghostscript is used in countries that use the international
% standard page size A4 rather than US letter, the page size of
% devices that default to letter or A4 can be changed by setting
% DEFAULTPAPERSIZE.[U]
/DEFAULTPAPERSIZE (a4) def[/U]
% Debian: Libpaper's default is in DEFPAPERSIZE; use that if the
%         current device is not "cups".
currentdict /DEFPAPERSIZE known
currentdict /DEVICE known { DEVICE } { () } ifelse
(cups) ne and
  { DEFPAPERSIZE /PAPERSIZE where { pop pop } { /PAPERSIZE exch def } ifelse }
if

```
Hope, this will help other people having the same problem.

---

### Post by stchman on 2008-01-17
> **feradz said:**
> Hi,

My printer always prints Letter format instead of A4.

After I installed Edgy, I experience very frustrating problem with my printer when I print **PDF** and **PS** files. When I print a PDF or PS the printer (Laser Jet HP3390) gives a warning message that there is no loaded Letter format. When I agree to continue printing it prints in Letter format.

I read a lot of staff about configuring and setting up a CUPS printer but ultimately I couldn't figure out how to fix this problem. I suppose this is a bug.

Besides I did all the recommended things in all available forums an mail lists:
1. /etc/papersize is A4
2. I updated the /usr/share/gs-esp/8.15/lib/gs_init.ps to be A4
3. My printer settings are A4
4. My regional settings are Spain (where the default paper size is A4)

Notes about my configuration:
1. Printer: Laser Jet HP3390
2. Network printer
3. Use hpijs instead of recommended postscript (although I tried it with the postscript)

I would highly appreciate your comments and suggestions about to fix this printer problem. 

Thanks,
Ferad Zyulkyarov

I found that using the CUPS web based software was the best.  Run the following command in a terminal:

```
firefox loclahost:631
```

Or bring up firefox and type localhost:631 in the URL box.

Go to your printer and make sure the paper is set to A4.  It should cure your problem.

---

