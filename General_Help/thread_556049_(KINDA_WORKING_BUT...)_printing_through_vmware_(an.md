---
title: "(KINDA WORKING BUT...) printing through vmware (any idea)"
date: 2007-09-20
forum: General Help
---

### Post by Weyoun on 2007-09-20
THERE IS NO LINUX DRIVERS FOR lEXMARK 2400 SERIES SO I INSTALLED WIN XP ON VMWARE SERVER TO MAKE IT WORK. I WANTED NETWORK PRINTING THROUGH VMWARE AND I KINDA DID IT BUT...
I SET UP BRIDGED NETWORK HOST (KUBUNTU) AND GUEST (WINXP). THEN IN PRINTING SECTION I CHOOSE SAMBA PRINTING AND IN HOST SECTION IP ADDRESS OF WINXP AND USRNAME AND PASS (THE ONES I CREATED BEFORE) THEN I CHOOSE RAW PRINTER (WITHOUT DRIVERS) AND THEN I TRIED TO PRINT.
HOST DID SENDD A SIGNAL TO GUEST OS AND IT STARTED TO PRINT (KINDA). IT WAS COUNTING PROGRESS ''PRINTING STARTED'' 1%, 5%........100% ''PRINTING COMPLETE'' LIKE EVERYTHING WORKS FINE BUT NOTHIN CAME OUT OF THE PRINTER
I'M OUT OF IDEAS SO PLEASE...
ANYONE

---

### Post by fjgaude on 2007-09-21
Wouldn't you have to install the Windows printer driver that came with the printer, install it just like you did when running straight Windows, but this time in the guest XP?

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by Weyoun on 2007-09-23
WELL OFF COURSE I INSTALLED THE PRINTER DRIVERS ON GUEST. I HAVE DONE EVERYTHING WHAT YOU DO NORMALLY WHEN YOU PLUG IN THE NEW DEVICE. I EVEN TESTED IT FROM WITHIN WINXP (GUEST) AND IT WORKS FINE LIKE THAT. BUT THERE WAS A PROBLEM WHEN I TRIED VIRTUAL NETWORK PRINTING. EVEN THEN EVERYTHING SEEMED FINE (ON THE SCREEN) BUT NOTHING CAME OUT OF THE PRINTER.
DAMN I HATE LEXMARK ! :mad:

---

### Post by R.Bucky on 2007-09-23
That happened to me last night. You have to go to the VMware server toolbar named "VM" and then to "Removeable Devices". You should see your printer there - so click on it. That should work

---

### Post by Weyoun on 2007-09-24
In ''vm'' Toolbar Printer Is Checked. 
I Did Every ''normal' Stuff!
The Problem Is That Printer  Does Not ''spit Out'' The Document I Want To Print, Nevertheless All That Printing Process You See On The Screen Like  Counting 1%-100%, And The Stupid Voice ''printing Started'' And ''printing Complete'' Is Perfectly Fine, All That Process Is Great, Like It Has Done The Job.
:)at Least It Is Fun To Mess Around, Looking For Answers:) And If We Do It, That Can Be Really  Helpful For Lots Of People!

---

