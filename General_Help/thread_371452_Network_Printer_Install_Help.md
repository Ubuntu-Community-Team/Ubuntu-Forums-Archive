---
title: "Network Printer Install Help"
date: 2007-02-26
forum: General Help
---

### Post by HessiaNerd on 2007-02-26
I was having a little trouble installing my Brother 420CN on the network

I followed this guide (for Kunbuntu) and it got me pretty far

[https://help.ubuntu.com/community/PrintersBrotherMfc420cn](https://help.ubuntu.com/community/PrintersBrotherMfc420cn)

the printer showed up in my printers, I changed the URI to ipp://192.168.0.105:9100 (where it shows up on the DHCP client table from my router)  but then I get stuck.  It wont print the test page and I really dont know what else to do...  The only thing I could think that went wrong is here:

```

***$ sudo dpkg -i cupswrappermfc420cn_1.0.0-1_i386.deb

Selecting previously deselected package cupswrappermfc420cn.
(Reading database ... 117096 files and directories currently installed.)
Unpacking cupswrappermfc420cn (from cupswrappermfc420cn_1.0.0-1_i386.deb) ...
Setting up cupswrappermfc420cn (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC420CN
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!
```


also the scanner portion does not seem to work.  I got this message when following the install instructions linked above:

```

***$ brsaneconfig2 -a name=MFC-420CN model=”MFC-420CN” nodename=SLEASY_P
Invalid model name
***$ brsaneconfig2 -a name=MFC-420CN model=”MFC-420CN” nodename=192.168.0.105
Invalid model name
```

Any tips would be greatly appreciated.

---

### Post by tgalati4 on 2007-02-27
In a browser:

localhost:631

CUPS is the unified printing system in Linux.  Mastering CUPS will give you insight into new ways to print and to troubleshooting problems.

What is the status of the printer as displayed by localhost:631/printers

What are the relevant errors in /var/log/cups

CUPS is pretty well-behaved, but you need to dig into the details to find out what is going on.  It's not plug and play, but once it is set up, it works pretty well.

Good luck!

---

### Post by HessiaNerd on 2007-02-27
Wow, awesome,  I had no Idea where to start.

Here is the printer 

```

MFC420CN "Network host '192.168.0.105' is busy; will retry in 30 seconds..."
	Description: MFC420CN
Location: 192.168.0.105
Make and Model: Local Raw Printer
Printer State: processing, accepting jobs, published.
Device URI: ipp://192.168.0.105
```

and here is the error log (via: [http://localhost:631/admin/log/error_log](http://localhost:631/admin/log/error_log))

```

 [26/Feb/2007:18:21:19 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [26/Feb/2007:18:21:19 -0800] [cups-driverd] Unable to open "/usr/share/ppd/brmfc420cn_cups.ppd" - No such file or directory
E [26/Feb/2007:18:21:19 -0800] copy_model: empty PPD file!
E [26/Feb/2007:18:21:19 -0800] PID 3307 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!
E [26/Feb/2007:18:23:40 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [26/Feb/2007:18:24:16 -0800] PID 3466 (/usr/lib/cups/backend/usb) crashed on signal 9!
... Quite a few of these........
E [26/Feb/2007:18:25:14 -0800] PID 3609 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [26/Feb/2007:18:26:19 -0800] cupsdAuthorize: Local authentication certificate not found!
.... and these.....


```

based on: **empty PPD file!** and **lpadmin: Unable to copy PPD file!** I would say this is the source of my problems....
> PostScript Printer Description ("PPD") files describe the capabilities of each printer and are used by CUPS to support printer-specific features and intelligent filtering.

so do I reinstall cupswrappermfc420cn_1.0.0-1_i386.deb  to get the correct PPD?  Can I get it somewhere else and put it where it is looking for it?

---

### Post by HessiaNerd on 2007-02-27
ARRG!

reinstalling using sudo dpkg -i gives me the same error, **lpadmin: Unable to copy PPD file!**

peaking into the .deb files I cannot identify the PPD, but I dont really know what to look for (i assume it would have PPD in the filename.

CAN SOMEONE HELP ME PLEASE!

Where can I get this PPD file, and where should I put it????  I need this to work!  Ubuntu is USELESS if I cant even print!!

---

### Post by HessiaNerd on 2007-02-27
ok... I found this:
> 

    * I'm using Ubuntu6.10. When installing the CUPS Wrapper driver, I get the following error message: "lpadmin:Unable to copy PPD file".

      1.
      Install the LPD/LPRng printer driver and CUPS Wrapper printer driver from the following pages:

      Note:
      It is important to install the LPD/LPRng driver before installing the CUPS Wrapper driver.

      (LPD/LPRng printer driver)
      [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

      (CUPS Wrapper printer driver)
      [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)


      If you receive the error message "lpadmin : Unable to copy PPD file" , please ignore it.

      Connect the printer to your Linux PC and turn the printer power on.

      2.
      Next, you have to check the DeviceURL.

      If you are connecting the machine via USB, run the command:
      " lpinfo -v".
      All device URL’s which are registered will be listed.

      If you are connecting the machine via the network or parallel port, enter the
      temporary DeviceURL "usb:/dev/usb/lp0" in the lpadmin command below.

      3.
      Next, check the PPD file name.
      Run the command:
      "ls /usr/share/cups/model" and check the PPD file name.


      4.
      Then you should run the following command:
      lpadmin -p (printer name) -E -v (DeviceURL) -P /usr/share/cups/model/(PPD file name)

      For example, the command should read like this:
      lpadmin -p HL2070N -E -v usb:/dev/usb/lp0 -P /usr/share/cups/model/brhl2070n.ppd

      Note:
      For "(DeviceURL)", please replace it with the DeviceURL you checked in Step2.
      For "(PPD file name)", please replace it with the PPD file name you checked in the Step3.


      5.
      If you are connecting the machine via the network, open the CUPS Web Interface "http://localhost:631/printers" , and change the DeviceURL to "lpd://xx.xx.xx.xx/binary_p1" or" lpd://nodename/binary_p1 ".
via: [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html)

and with a little tweaking, it seems to work!   \m/

just low on ink

---

### Post by tgalati4 on 2007-02-27
Great status report.  This is an good example of how the forums work.  Point someone in the right direction and let them run wild!

Linux can't help you with the ink problem.  That's a monopoly of a different source.  At least we can free ourselves from software oppression.

Now, put a pinhole for port 631 in your firewall, set "allow" for a range of sensible IP numbers in the CUPS configuration file, and you can print remotely from a friend's house.  Comes in handy when they run out of ink!

Please share your newfound Linux knowledge with others.

---

### Post by HessiaNerd on 2007-02-28
thank you for the help...

Im going to look into remote access in the future though...  Im keeping pretty busy just trying to get everything up and running at the moment.  The forums have been great help so far, Ive been very impressed with the amount of help Ive received.

---

