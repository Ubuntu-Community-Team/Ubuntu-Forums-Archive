---
title: "Hylafax server and client installation"
date: 2008-03-21
forum: General Help
---

### Post by satimis on 2008-03-21
Hi folks,


Archlinux 86_64 2007-08-2 (as workstation)
Evolution - mail client
GNOME desktop

Ubuntu 7.04 server amd64 (as mail server)
Postfix - mail server
HylaFax server


I'm prepared to setup following faxing service on Archlinux;

1)
Send fax direct on application, such as OOo, gedit, etc., with print command.  It is similar to Symantic WinFax on Windows working as a Windows printer.


2)
Email to fax
Send fax as email via HylaFax server on Ubuntu.  Fax will be saved as .pdf/.tiff format and attached to the email to dispatch.  The email body will be the cover page.


But I can't figure out how to achieve my goal.  Could you please shed me some light.  TIA



1)
Send fax direct on application

I found "WinPrint HylaFax" which is a suitable application for this purpose.  

[https://sourceforge.net/projects/winprinthylafax/](https://sourceforge.net/projects/winprinthylafax/)

But it runs on Windows.  I don't consider running it on "wine" (I have no idea whether it runs on "wine" or not)

Then I found gfax;

[http://www.cowlug.org/gfax/](http://www.cowlug.org/gfax/)


I don't know whether it can achieve my goal - "send fax direct on application with "Print"?  Any other suggestion?


Do I still need installing HylaFax on Archlinux?



2)
Email to fax

Do I need install HylaFax on Archlinux?  OR make use of the Ubuntu mail server for its dispatch?


Thanks


Furthermore

$ apt-cache search hylafax+```

capi4hylafax - Faxing over CAPI 2.0 device
ghfaxviewer - The GNU HaliFAX Viewer
gnue-reports - An XML-based output-independent reporting system
hylafax-client - Flexible client/server fax software - client utilities
hylafax-doc - Flexible client/server fax software - HTML Documentation
hylafax-server - Flexible client/server fax software - server daemons
iaxmodem - software modem with IAX2 connectivity
libfax-hylafax-client-perl - Simple Perl client for HylaFAX fax server

```
Which packages I need to install?


B.R.
satimis

---

### Post by k|d&lt;FuNkY&gt;FrY on 2008-03-25
I'm in the beginning stages of setting up something exactly along these same lines. I will follow up on this thread shortly.

---

### Post by rev0lv3r on 2008-06-12
Any update
I am also trying to setup a Halyfax server
WinFax is no longer supported and won't even install and run properly thanks to some changes in SP2 or SP3, even the 10.04 update doesnt work properly
Oh well

Hylafax doesn't seem too difficult

I just can't seem to get it installed correctly on the server
From there it seems easy, just a matter of getting a proper client / connector and a print driver for your client

I've heard one can use the "lspci" command to find out if their modem is detected properly
Are there any other things to run to check modem (if it's linux compatible and what not?)

---

