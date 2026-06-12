---
title: "Google Chrome print problems"
date: 2013-06-16
forum: General Help
---

### Post by Cloudy Brain on 2013-06-16
I recently had to install Google Chrome so my 5yr old could play a flash game (for whatever reason it just wouldn't get past a certain point with Firefox). I made it the default browser so he could get on and play it by himself. Then my wife found that she couldn't print anything from it, the print preview appears to hang, never renders a preview and never enables the print button.

Does anyone else have this problem or is it just me? The About page says I've got v[COLOR=#303942][FONT=Ubuntu]ersion 27.0.1453.110[/FONT][/COLOR]

I discovered that it's possible to bypass the print preview with <Ctrl>+<Shift>+P and printing works through the system dialog, and I've now modified the launcher to include the --disable-print-preview switch found here [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

```

sudo cp /usr/share/applications/google-chrome.desktop /usr/share/applications/google-chrome.orig-desktop
gksudo gedit /usr/share/applications/google-chrome.desktop &

```

Add the switch on the first Exec line;

```

Exec=/opt/google/chrome/google-chrome --disable-print-preview %U

```

I hope that might help someone who has the same problem. It's not a fix, just a temporary work around.

---

### Post by gordintoronto on 2013-06-17
It might be useful to mention what version of Ubuntu you are using, and perhaps what printers you have installed.

I have not had any problem printing from Chrome.

---

### Post by Cloudy Brain on 2013-06-17
@gordintoronto thanks for replying and you're absolutely right, I should have given more details.

I have my main desktop and a server, both are Ubuntu 12.04.2 LTS (I can't yet change my forum user profile). The server has the printers physically attached. The printers are a Canon iX6550 and an Epson AL M1200. The Canon driver is an 'offical' Canon one, the Epson one is a foomatic driver for the 6200L series printer I compiled from source [1]. My desktop (and other machines) connect to the printers over ipp as ipp://<server>/printers/<printer>

I read in an old bug report of a similar nature [2] to check in the ~/.xsession-errors, and this is what I get:

```

[2581:2581:0616/220130:ERROR:CONSOLE(811)] "Google Cloud Print Error: HTTP status 403", source: chrome://print/print_preview.js (811)
[2581:2627:0616/220133:ERROR:print_backend_cups.cc(241)] CUPS: Failed to get PPD, printer name: EpsonM1200
[2581:2581:0616/220133:ERROR:CONSOLE(2951)] "Failed to get print capabilities for printer EpsonM1200", source: chrome://print/print_preview.js (2951)

```

I haven't knowingly enabled Cloud Print...

Many thanks in advance if you can shed some light on this

[1] [http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)
[2] [https://code.google.com/p/chromium/issues/detail?id=140648](https://code.google.com/p/chromium/issues/detail?id=140648)

---

### Post by gordintoronto on 2013-06-17
Sorry, it's years since I have needed to fool around with printer drivers. I run Printing and click on Add, click on Network Printer and wait a few seconds. Highlight my printer, then say "Yes," "OK" or "continue" until the printer is installed and working. On average, I try one new distro or version a month, and for about three years this procedure has worked for the Brother laser attached to my router.

I suggest you try it.

---

### Post by pdc on 2013-06-17
we have Version 27.0.1453.93 of Chrome installed; 32bit 12.04LTS; Canon MG3160 printer; it prints well; and has always when I think back............as I have printed various street maps with it 

this is only a chrome issue for you?

---

### Post by Cloudy Brain on 2013-06-18
@gordintoronto many thanks for your kind help.

@pdc, yes it's only from within Chrome's print preview that I have the problem. All of my machines (desktop mentioned above, a laptop and a mythtv box all running 12.04 x64) can successfully print using the system print dialog. Chrome prints fine too so long as I bypass the print preview - hence my hack above.

It's obviously the way I've got the machines set up; only the server has the printer drivers and possibly the clients don't have (shouldn't need?) the drivers/PPD's and that's why Chrome is failing. I don't really know whether that setup is correct, but it works for all machines, and if it ain't broke...

For now I'm not too bothered about not using the print preview, it just slightly irks me that I can't figure it out!

---

### Post by Julian_Seewald on 2013-09-09
I had a similar issue

i run Ubuntu 12.04 LTS and Google Chrome [COLOR=#303942][FONT=Ubuntu]29.0.1547.65.
i print on a HP 2055 LserJet connected via SAMBA on a Windows Server

i can print perfectly from Ubuntu but when i preview sth to print, after sending it to the printer, it hangs the whole printer queue (for every user on the lan), on the printer display i see "Memory Error", after reseting the printer and the Ubuntu printer queue it restarts fine.

disabling Google Cloud Print solved the issue[/FONT][/COLOR]

---

