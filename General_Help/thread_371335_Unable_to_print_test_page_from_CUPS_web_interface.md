---
title: "Unable to print test page from CUPS web interface"
date: 2007-02-26
forum: General Help
---

### Post by eradicator_006 on 2007-02-26
I have a Ubuntu Dapper server setup and am having a problem when trying to print a test page from the cups web interface.  I get the error message "Unsupported format 'application/postscript'!".  The printer is a HP Laserjet 6L.  I've tried using every laserjet driver available and have the same results with all drivers.  Now, this isn't really a major problem because I am able to print with no problems from all of my samba clients (mac and win xp).  It would be nice to know why I am unable to print from the server itself.  Any input would be appreciated.

Thanks

---

### Post by crispy_420 on 2007-02-26
My guess is your printer is not properly installed.

Do you have the printer installed? Are you able to print a test page? 

Here is some stuff I found:

[http://ubuntuforums.org/showthread.php?t=239772&highlight=3940](http://ubuntuforums.org/showthread.php?t=239772&highlight=3940)

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L)

Take a look at those links.

---

### Post by eradicator_006 on 2007-02-26
> **crispy_420 said:**
> My guess is your printer is not properly installed.

Do you have the printer installed? Are you able to print a test page? 

Here is some stuff I found:

[http://ubuntuforums.org/showthread.php?t=239772&highlight=3940](http://ubuntuforums.org/showthread.php?t=239772&highlight=3940)

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L)

Take a look at those links.

Thanks, I think I read all that info already.  The printer is installed correctly because I am able to print to it from samba clients.  I have configured samba to use CUPS for printing.  I just can't print a test page from the cups web interface.

---

### Post by johnc4510 on 2007-02-26
Have you registered and set up your printer at the cups web site?

---

### Post by llamakc on 2007-02-26
What do your logs say?

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> What do your logs say?

/var/log/cups/error.log:
I [26/Feb/2007:19:17:53 -0600] Print-Job client-error-document-format-not-supported: Unsupported format 'application/postscript'!
D [26/Feb/2007:19:17:53 -0600] cupsdProcessIPPRequest: 11 status_code=40a (client-error-document-format-not-supported)
D [26/Feb/2007:19:17:54 -0600] [CGI] cgiCopyTemplateLang(tmpl="header.tmpl")
D [26/Feb/2007:19:17:54 -0600] [CGI] locale="en"...
D [26/Feb/2007:19:17:54 -0600] [CGI] Template file is "/usr/share/cups/templates/header.tmpl"...

---

### Post by llamakc on 2007-02-26
Do you have an /etc/cups/mime.types and /etc/cups/mime.convs?

---

### Post by llamakc on 2007-02-26
If not, your "cupsys" install is fubar'd. You can remove & purge the cupsys package, and reinstall it.

```

cd ~ && sudo apt-get remove --purge cupsys && sudo apt-get install cupsys
```

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> Do you have an /etc/cups/mime.types and /etc/cups/mime.convs?

Yes I do.  I didn't make any changes to those files at all.  All I did was installed cupsys and the cups-gutenprint drivers.  I then modified the cupsd.conf file so I can connect to the web interface from my machine.  I then added the cups user to the shadow group so the web interface authentication works properly.  Then I added the printer using the web interface and I get the error message no matter which driver I use.  After the test page didn't work, I  configured sama to use cups for printing.  No problems printing through samba.

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> If not, your "cupsys" install is fubar'd. You can remove & purge the cupsys package, and reinstall it.

```

cd ~ && sudo apt-get remove --purge cupsys && sudo apt-get install cupsys
```

Tried that 3 times already.  Thanks though.

---

### Post by llamakc on 2007-02-26
> **eradicator_006 said:**
> Tried that 3 times already.  Thanks though.

So you DO have those files in /etc/cups? And you have purged the packages, instead of just removing them?

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> So you DO have those files in /etc/cups? And you have purged the packages, instead of just removing them?

That's right.  I purged them, did a rm -rf /etc/cups, reinstalled all cups packages and it didn't help.

---

### Post by llamakc on 2007-02-26
Have you checked the bugs against cupsys? What packages do you have installed? Are you using gutenprint?

What's the output (in a terminal) of `dpkg -l |grep cups`

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> Have you checked the bugs against cupsys? What packages do you have installed? Are you using gutenprint?

What's the output (in a terminal) of `dpkg -l |grep cups`

Finally found a fix at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381743](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381743)  Looks like it's a bug.

Basically a config file does not get created when it should.  /etc/cups/pstoraster.convs should contain:

application/vnd.cups-postscript application/vnd.cups-raster     100     pstoraster



Heres the output of dpkg -l | grep cups  (*Note, the problem happens with and without the gutenprint drivers installed)

i  cupsys                          1.2.2-0ubuntu0.6.06           Common UNIX Printing System(tm) - server
ii  cupsys-bsd                      1.2.2-0ubuntu0.6.06           Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                   1.2.2-0ubuntu0.6.06           Common UNIX Printing System(tm) - client pro
ii  cupsys-driver-gutenprint        5.0.0~rc2-0ubuntu6            printer drivers for CUPS
ii  libcupsimage2                   1.2.2-0ubuntu0.6.06           Common UNIX Printing System(tm) - image libs
ii  libcupsys2                      1.2.2-0ubuntu0.6.06           Common UNIX Printing System(tm) - libs

---

### Post by llamakc on 2007-02-26
By adding that file or contents in that file, were you able to resolve this?

---

### Post by eradicator_006 on 2007-02-26
> **llamakc said:**
> By adding that file or contents in that file, were you able to resolve this?

Yes.  I just had to create that file with the one line in it.

---

