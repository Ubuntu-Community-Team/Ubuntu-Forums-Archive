---
title: "SAP Printing"
date: 2008-04-23
forum: General Help
---

### Post by bryle on 2008-04-23
I'm able to install SAPGui for Java on Ubuntu 7.04 and its working properly. The problem is that i can't print SAP Documents, is it because there's no SAPlpd? I really appreciate your help on how to make this work. Can someone give me a link where I can follow some instructions on how to about this. Thanks

Bryle

---

### Post by chronos00 on 2010-02-04
I'm am sorry to revive this thread, but since it didn't had any answers, it is perhaps for the best.

I have the exact same problem as stated in the first post. I have migrated from Wind0ze to Ubuntu. I could previously print any document in SAP using my local printer. This is no t possible using SAP GUI for Java.
I am currently using version 7.2

Thanks in advance!

---

### Post by gdecoster on 2010-03-15
Local printing in SAPGUI for java is supported using access method 'G' (as of SAP Web AS 6.20)
See OSS note 821519 for more information.

---

### Post by chronos00 on 2010-03-16
thanks for the info gdecoster!

I have searched everywhere for Online SAP Support notes, but came empty handed. Could you please point me to OSS note 821519?

I'll need to read this, but I can tell you that I already tried access method 'G' from the Java GUI. So far I couldn't make it promt for any local printer...

I will try whatever the OSS note suggests.

---

### Post by gdecoster on 2010-03-16
You can find OSS notes on SAP's support site (SAP Service Marketplace) at service.sap.com. You need a user ID to access this site. If you don't have one, ask your SAP Basis guy to get the note for you.

I gathered that you are on a SAP release that provides access method 'G' for local printing and that you have SAPGUI for Java version 7.20 installed on your desktop.

Can you check how the local device was defined in SPAD ? It should look similar to this:
Output device		: Local
Short nane		: LOCL
Device type		: HPDJ850 : HP Deskjet 850C
Device class		: Standard printer
Host spool access method : G: Frontend print with control technologie
Host printer		: __DEFAULT	(two underscore characters)

The device type needs to match your actual printer as closely as possible. If you know your printer can handle Postscript, you can specify POST2 here.
Host spool access method needs to be 'G'. SAPGUI for Java does not support 'F'.

When you print to this local device (with the 'print immediate' option checked and the 'Delete after output' option unchecked), does it show up in the SAP spool ? Do you see the print request in status 'Compl.' in SP02 ?

I never get prompted for a local printer (maybe because I only have one) but I got it to work after I defined my local printer in SAPGUI for java.
To check this, go to menu option 'File' -> 'Preferences' in the guilogon window. Go to the 'Desktop-Printing' Preferences and make sure your local printer is set in field 'Default Queue'.

Hope this helps

---

### Post by chronos00 on 2010-03-17
> **gdecoster said:**
> You can find OSS notes on SAP's support site (SAP Service Marketplace) at service.sap.com. You need a user ID to access this site. If you don't have one, ask your SAP Basis guy to get the note for you.

Oh... that's the reason I couldn't find any documentation...

> I gathered that you are on a SAP release that provides access method 'G' for local printing and that you have SAPGUI for Java version 7.20 installed on your desktop.
That is correct.

> Can you check how the local device was defined in SPAD ? It should look similar to this:
Output device		: Local
Short nane		: LOCL
Device type		: HPDJ850 : HP Deskjet 850C
Device class		: Standard printer
Host spool access method : G: Frontend print with control technologie
Host printer		: __DEFAULT	(two underscore characters)
Almost identical. I couldn't use "HPDJ850" or any similar device type since the printers I was using is not listed. Instead, I was using "PDF1: PDF ISO Latin-1" wich almost worked.

> The device type needs to match your actual printer as closely as possible. If you know your printer can handle Postscript, you can specify POST2 here.
I just tried POST2, and it sometimes performs better than PDF, so L'll try to stick with it. Thanks for the tip!

> Host spool access method needs to be 'G'. SAPGUI for Java does not support 'F'.
Done.

> When you print to this local device (with the 'print immediate' option checked and the 'Delete after output' option unchecked), does it show up in the SAP spool ? Do you see the print request in status 'Compl.' in SP02 ?
This is exactly other problem I have... Thanks to what you said, I found the option to "immediate print". The problem is that I can't make this configuration stick! Every time I log in, and want to print something, after choosing the printer I need to change the option from "leave in spool" (or something like it since I have a spanish translation) to "print immediate". Is there any way to make this the default configuration?

> I never get prompted for a local printer (maybe because I only have one) but I got it to work after I defined my local printer in SAPGUI for java.
To check this, go to menu option 'File' -> 'Preferences' in the guilogon window. Go to the 'Desktop-Printing' Preferences and make sure your local printer is set in field 'Default Queue'.

Hope this helps

I have several printers configured in my system, but when printing, I am not promted to choose. It either prints or it doesn't.

**==================================================**

What I found out is that the default configuration of SAPGUI for Java sends the print job to: "lp -d %p -n %n %o" (You will see this in 'Desktop-Printing' Preferences of SAPGUI). The problem in this command is that it fails to handle printers with spaces (and won't return any errors).

```
lp -d "printer name" -n "number of copies" "file(s)"
```

If you just run "lp" with no arguments, it will just print to the default printer, only one copy. Which is just fine for me.


**So, to sum up:**

Printer configured as:
```
Device type		: POST2
Device class		: Standard printer
Host spool access method : G: Frontend print with control technologie
Host printer		: __DEFAULT	(two underscore characters
```

Printing preferences in JAVAGUI:
```
change "lp -d %p -n %n %o" to "lp" or something that works acording to the use of "lp"
```

Thanks for your help gdecoster! Couldn't have done it without your help!

---

### Post by gdecoster on 2010-03-17
Glad it works.

And yes, you can make the 'print immediate' option stick. It is set in your user profile.
In a SAPGUI for Java window, go to menu option 'System -> User profile -> Own data' (or just run transaction SU3). Go to the 'Defaults' tab. In the 'Output Controller' section you can specify the default value for the output device, the 'print immediate' option and the 'delete after output' option.

---

