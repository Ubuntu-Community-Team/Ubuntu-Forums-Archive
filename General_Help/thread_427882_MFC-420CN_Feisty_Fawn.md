---
title: "MFC-420CN Feisty Fawn"
date: 2007-04-29
forum: General Help
---

### Post by Lokithor on 2007-04-29
I have a Brother MFC-420CN installed as a network printer.

Ubuntu 7.04 recognized the printer and gave me the 3-step printer install screen, which I completed.

I then attempted to send a Test Page.
The printer icon showed "1 Print job", then the message cleared as if the print job was completed.
I went into the room that houses my printer - nothing was printed. I tried this several times.  I also sent a document from Open Office - nothing printed.

Any suggestions?

---

### Post by dcstar on 2007-04-30
> **Lokithor said:**
> I have a Brother MFC-420CN installed as a network printer.

Ubuntu 7.04 recognized the printer and gave me the 3-step printer install screen, which I completed.

I then attempted to send a Test Page.
The printer icon showed "1 Print job", then the message cleared as if the print job was completed.
I went into the room that houses my printer - nothing was printed. I tried this several times.  I also sent a document from Open Office - nothing printed.

Any suggestions?

The Brother web site has special Linux software and driver files, you may want to have a look and see if there is something for your model (I needed them for my HL-2040).

---

### Post by intMain on 2007-05-28
> **Lokithor said:**
> I have a Brother MFC-420CN installed as a network printer.

Ubuntu 7.04 recognized the printer and gave me the 3-step printer install screen, which I completed.

I then attempted to send a Test Page.
The printer icon showed "1 Print job", then the message cleared as if the print job was completed.
I went into the room that houses my printer - nothing was printed. I tried this several times.  I also sent a document from Open Office - nothing printed.

Any suggestions?

That auto install process did not work for me either.  Use this guide to help you setup your MFC420CN.

[https://help.ubuntu.com/community/PrintersBrotherMfc420cn](https://help.ubuntu.com/community/PrintersBrotherMfc420cn)

---

### Post by intMain on 2007-06-02
Lokithor, if you haven't checked your PM, here is the solution to your problem with the invalid nodename.

You had:

**brsaneconfig2 -a name=MFC-420CN model=MFC-420CN [COLOR="Red"]192.168.2.2=MFC-420CN[/COLOR]**

Suppose to be:

**brsaneconfig2 -a name=MFC-420CN model=MFC-420CN [COLOR="Blue"]ip=192.168.2.2[/COLOR]**

If you use the "ip" option it would be "ip=<ip_address>" or it'll be "nodename=<nodename>".  The nodename can be found in the CUPS web config ([http://localhost:631](http://localhost:631)) selecting your found printer. In this case it would be mfc-420cn unless you've changed it before.

---

### Post by Statik on 2007-06-20
What do you do if you DON'T want it to use the network, but the USB. Mine keeps reverting to the slower IP address access.

Statik

---

