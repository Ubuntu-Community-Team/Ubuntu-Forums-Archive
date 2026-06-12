---
title: "subprocess post-removal error"
date: 2008-05-25
forum: General Help
---

### Post by Robbyx on 2008-05-25
What should I do:

```
robin@robin:~$ sudo deborphan | xargs sudo apt-get -y remove –purge
sudo: deborphan: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package –purge
robin@robin:~$ sudo apt-get install deborphan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dialog
The following packages will be REMOVED
  brscan2
The following NEW packages will be installed
  deborphan dialog
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/330kB of archives.
After this operation, 1786kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 137573 files and directories currently installed.)
Removing brscan2 ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Robin

---

### Post by ibuclaw on 2008-05-25
Where did you get the package "**brscan2**" from?

Did it come with your printer? (Noting the trademark name Brother).

Try installing with aptitude. Just type in "**sudo aptitude**" in the terminal.
Then follow this key combo.
```

**Ctrl+T**        Opens Menu Bar.
**Left**          Navigate Left.
**Left**
**F**             Selects the Option to view packages as flat.
**L**             Open Search Box.
**deborphan**
**Enter**
**+**             Mark deborphan to install.
**G**             Go to confirmation page.

```
Then use the arrow keys to highlight **brscan2**. And press the equals sign```
=
```to mark is as hold.
Then Press **G** to continue to install the packages.

If it still won't let you.
Type in:
```
apt-get install -f
```
To force the removal of it.

Regards
Iain

---

### Post by Robbyx on 2008-05-25
> **tinivole said:**
> Where did you get the package "**brscan2**" from?

Did it come with your printer? (Noting the trademark name Brother).

Try installing with aptitude. Just type in "**sudo aptitude**" in the terminal.
Then follow this key combo.
```

**Ctrl+T**        Opens Menu Bar.
**Left**          Navigate Left.
**Left**
**F**             Selects the Option to view packages as flat.
**L**             Open Search Box.
**deborphan**
**Enter**
**+**             Mark deborphan to install.
**G**             Go to confirmation page.

```
Then use the arrow keys to highlight **brscan2**. And press the equals sign```
=
```to mark is as hold.
Then Press **G** to continue to install the packages.

If it still won't let you.
Type in:
```
apt-get install -f
```
To force the removal of it.

Regards
Iain
Thank you for your quick response. 

I tired to install deborphan as per your instructions above, but there was an error message.

[B]I wasn't able to locate file for the brscan2 package. This might mean you need to manually fix this package.
Internal error: couldn't generate list of packages to download.[/B]

The Brscan2 package is the brother scanner package which I am meant to uninstall and then reinstall but it would not properly uninstall nor allow a reinstall.

Robin

---

### Post by ibuclaw on 2008-05-25
You could try the (slightly clean, but very sneaky) manual way of removing brscan2.
[LIST]
[*]Change directory to the dpkg info folder:
```
cd /var/lib/dpkg/info
```
Locate all brscan2 files.
```
ls -1 | grep brscan2
```
Then open the file ending with the suffix "**.postrm**" as root.
ie:
```
sudo gedit brscan2.postrm
```
Then locate all matches of this pattern from within the file:
```
exit $?
```
And change it to "**exit $0**"

Save the change and try to uninstall it again.
The post-remove script should return with the right code for the app to be successfully removed.
[/LIST]

Regards
Iain**

---

### Post by Robbyx on 2008-05-25
brsan2.postrm contains only the following:

[B]#!/bin/sh
# ESP Package Manager v3.7.0
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData/ALL
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData/AL
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane
[/B]

Can you please suggest how I change it?

Robin

---

### Post by ibuclaw on 2008-05-25
append to the bottom of the file "**exit 0**":
[EDIT]
Also, if you want a clean output. Add "**2>/dev/null**" to the end of each line...
```

rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData/ALL 2>/dev/null
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData/AL 2>/dev/null
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane/GrayCmData 2>/dev/null
rmdir --ignore-fail-on-non-empty /usr/local/Brother/sane 2>/dev/null
exit 0

```

If you still get errors, delete all lines with the "rmdir" command.

Regards
Iain

---

### Post by Robbyx on 2008-05-25
Thank you very much for that help. I have been able to remove the driver and reinstall it. Unfortunately it still does not work so I have written to brother for further support. They had told me to alter the 45-libsane.rules file in etc/udev to 

[B]#BROTHER MFC-5460CN
SYSFS{idVendor}==”04f9”, SYSFS{idProduct}==”01b7”, MODE=”664”, GROUP=”scanner”[/B]

When I try to acquire an image from Gimp it reports:

[B]Failed to open device 'gt68xx:liusb:008:003'
[/B]

Do you have any experience in solving such a situation?

Robin

---

### Post by ibuclaw on 2008-05-25
Erm... It's not my strong point.
But looking at the config they gave you. I can easily say that I know what everything means in the line.

Can you post the output of
```
lsusb
```
while the scanner is still plugged in your USB port.

Thanks.

[EDIT]
Also, I couldn't help but notice that Ubuntu provides their own working version of the driver for you.
```
sudo apt-get install brother-cups-wrapper-bh7
```
Perhaps, you should use them instead of the sites version.

Regards
Iain

---

### Post by Robbyx on 2008-05-25
Thanks for trying. Here is the lsusb:

robin@robin:~$ lsusb
Bus 008 Device 005: ID 04f9:01b7 Brother Industries, Ltd 
Bus 008 Device 004: ID 043d:0014 Lexmark International, Inc. 
Bus 008 Device 003: ID 043d:002d Lexmark International, Inc. X70/X73 Scan/Print/Copy
Bus 008 Device 002: ID 043d:0029 Lexmark International, Inc. 
Bus 008 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 051d:0002 American Power Conversion 
Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  


Robin

---

### Post by Robbyx on 2008-05-25
> Also, I couldn't help but notice that Ubuntu provides their own working version of the driver for you.
Code:

sudo apt-get install brother-cups-wrapper-bh7

Perhaps, you should use them instead of the sites version.


As it is cups it is probably the printer driver not the scanner driver. Do you agree?

Robin

---

### Post by ibuclaw on 2008-05-25
> **Robbyx said:**
> As it is cups it is probably the printer driver not the scanner driver. Do you agree?

Robin

Ah, OK.
But you never know until you try it.

Also, have you switched your USB Ports at all in the time between you Posting the GIMP error message and you showing the output of lsusb?

As it seems that they contradict one another. (Either that or I've found your problem).

> Failed to open device 'gt68xx:liusb:**008**:**003**'
This tells me that GIMP "thinks" that your scanner is on the Bus 8, Device 3 port.

> Bus **008** Device **005**: ID 04f9:01b7 Brother Industries, Ltd 
But this tells me that the Brother Scanner is really on Bus 8, Device 5.

That may be the problem, but as to a fix, I'm not too sure.

Iain

---

### Post by Robbyx on 2008-05-25
Of course I  do not know either and so  I have sent an email to brother.

Thanks for your help and if you do think of an answer please post it.

Robin

---

### Post by PhoenixDream on 2009-07-11
Thanks guys as I have experienced exactly the same problem with my brother scanner/printer, moreso the scanner driver, since upgrading to Jaunty.

Problem is fixed, so much appreciated. :)

---

### Post by Terence Hood on 2010-05-06
> **Robbyx said:**
> Thank you very much for that help. I have been able to remove the driver and reinstall it. Unfortunately it still does not work so I have written to brother for further support. They had told me to alter the 45-libsane.rules file in etc/udev to 

[B]#BROTHER MFC-5460CN
SYSFS{idVendor}==”04f9”, SYSFS{idProduct}==”01b7”, MODE=”664”, GROUP=”scanner”[/B]

When I try to acquire an image from Gimp it reports:

[B]Failed to open device 'gt68xx:liusb:008:003'
[/B]

Do you have any experience in solving such a situation?

Robin

[COLOR=Sienna][B][COLOR=Black]In my experience with my lexmark x73 printer/scanner and this same gt68xx error it was that I needed to place a firmware file for my device in /usr/share/sane/gt68xx

I see that you seem to have a Lexmark X73 installed as well? I was able to locate my firmware from this site. Maybe it will help you too.[/COLOR]
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)[/B][/COLOR]

---

