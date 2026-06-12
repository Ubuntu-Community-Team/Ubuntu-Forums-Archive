---
title: "Epson WF-2530"
date: 2014-12-06
forum: General Help
---

### Post by Jodie_Miles on 2014-12-06
I have recently installed Ubuntu 14.10 onto my Samsung laptop and so far I much prefer it to Windows. Have found alternatives for some of them programmes I used in Windows (Itunes for instance) which are all working fine. The only issue I'm having is my Epson all in one printer (which I used wirelessly on Windows) won't install. 

The disc I have with the drivers doesn't work. I have been online to Epson Support to download the driver but no luck. I have also plugged the printer in with the USB cable, it shows but doesn't work, just comes up sending work to printer and that's as far as it goes.

I'm not a computer techy so need advice in laymans terms please but unless I can get this to work then I think I will have to go back to using Windows (not sure how I get it back though yet!).

Thank you for any advice.

---

### Post by vasa1 on 2014-12-06
> **Jodie_Miles said:**
> I have recently installed Ubuntu 14.10 onto my Samsung laptop and so far I much prefer it to Windows. Have found alternatives for some of them programmes I used in Windows (Itunes for instance) which are all working fine. The only issue I'm having is my Epson all in one printer (which I used wirelessly on Windows) won't install. 

...
I can't help you myself but if you mention the model of your Epson all in one printer, someone else might.

Meanwhile, here are some links I came across:
[https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners)
[http://askubuntu.com/questions/303642/installing-epson-printer-scanner](http://askubuntu.com/questions/303642/installing-epson-printer-scanner)
[http://askubuntu.com/questions/127600/how-do-i-get-an-epson-stylus-dx4450-all-in-one-printer-scanner-working](http://askubuntu.com/questions/127600/how-do-i-get-an-epson-stylus-dx4450-all-in-one-printer-scanner-working)
[https://www.youtube.com/watch?v=xOiynX8hc0Y](https://www.youtube.com/watch?v=xOiynX8hc0Y)
[http://tutorialforlinux.com/2014/08/23/how-to-install-epson-wf-2530-all-in-one-printer-drivers-quick-start-scanning-easy-guide/](http://tutorialforlinux.com/2014/08/23/how-to-install-epson-wf-2530-all-in-one-printer-drivers-quick-start-scanning-easy-guide/)
[http://ubuntuforums.org/showthread.php?t=2197576](http://ubuntuforums.org/showthread.php?t=2197576)
[https://answers.launchpad.net/ubuntu/+source/cups/+question/210252](https://answers.launchpad.net/ubuntu/+source/cups/+question/210252)

---

### Post by howefield on 2014-12-06
> **vasa1 said:**
> I can't help you myself but if you mention the model of your Epson all in one printer, someone else might.

You don't think it is in the title, do you ?

Try here : [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

---

### Post by ajgreeny on 2014-12-06
Exactly what Epson all in one printer is it?  
EDIT:  (Whoops, I didn't notice the model either)

The disk you got with it will no doubt have Windows and Mac drivers; Linux drivers will be totally absent, but many Linux drivers are available for Epson machines; we just need to know which you have.

You could also try using the cups webmin page in a web-browser.
Point your browser to **[http://localhost:631/](http://localhost:631/)** in the addressbar, go to **Administration** in the top menubar and click on **Add Printer**.  You will probably be asked for your username and user password, and can then start a search for the machine and drivers for it.  Depending on the model you may or may not be lucky, but it is certainly worth a try.

---

### Post by vasa1 on 2014-12-06
> **howefield said:**
> You don't think it is in the title, do you ?
...
Oops!

---

### Post by Jodie_Miles on 2014-12-06
Not listed i'm afraid :-(

---

### Post by howefield on 2014-12-06
Yes, it is. I'm afraid.

---

### Post by Jodie_Miles on 2014-12-06
Yes I had been through them files from Epson website and couldn't get anything to work, but the second one down has just installed it onto the computer. Looks like it can use it with USB cable so now got to work out how to set it up with the wifi again using linux.
Thank you

---

### Post by howefield on 2014-12-06
The add printer in system settings should pick it up under the Network Printer section, with any luck :)

---

### Post by ady2 on 2015-02-25
has anybody had any luck getting this printer to work I am struggling to find any drivers EPSOM WF 2530

---

### Post by pdc on 2015-02-26
Hi ady2

welcome to the Ubuntu forums

you don't tell us if you plan on a wireless connection

usually there are 3 steps with setting up a new printer

1) connect it
2) install the printer drivers
3) register it on your system

__________________________________

1) if you plan usb, ............. plug in that cable..............if you plan wireless, the printer needs to be accepted by the router: have you done that?

here is a video if you have not [http://www.epson.com/cgi-bin/Store/support/SupportShowVideo.jsp?BV_UseBVCookie=yes&oid=209709&void=225006](http://www.epson.com/cgi-bin/Store/support/SupportShowVideo.jsp?BV_UseBVCookie=yes&oid=209709&void=225006)

2) PRINTER DRIVERS

so you start here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in WF-2530 and it takes you to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff) and Ubuntu uses debian packages so if you have a 32bit system you need [COLOR="#008000"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_i386.deb[/COLOR] and if 64bit you need [COLOR="#008000"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb
[/COLOR]
-_______________________________--

for part 3), open the PRINTERS section of the administration menu; and there should be a big ADD NEW PRINTER button; and you can tell it you want to add the Epson;

__________________

let us know how you get along

---

