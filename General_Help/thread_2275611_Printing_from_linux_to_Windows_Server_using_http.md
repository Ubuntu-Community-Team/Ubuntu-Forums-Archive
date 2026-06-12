---
title: "Printing from linux to Windows Server using http"
date: 2015-04-27
forum: General Help
---

### Post by gavinw2 on 2015-04-27
Folks,

Can anyone offer any meaningful guidance for getting an Ubuntu Desktop (14.04.2) to print (via cups) over http to a Windows Server 2012 machine.
The windows box has "Internet Printing" installed and an HP MFD M630 attached as a shared network printer.

I can view the printer using [http://server/printers](http://server/printers) from both the windows box and the Ubuntu box.

On the Ubuntu box I have cups 1.7.2 installed and HPLIP 3.14.2 installed (I don't think HPLIP is actually needed for printing but I did use it to identify the appropriate PPD file).  I have added the printer using the URL [http://server/printers/printer_name/.printer](http://server/printers/printer_name/.printer).
However, when I print (from chrome) to the printer I usually end up with a print job stuck in the queue on the Ubuntu box with a status of "Held for Authentication".  Using right-click Authenticate and supplying valid domain credentials does not help.
On the Windows box we have tried setting authentication to "Windows authentication", to "Basic authentication" and to "anonymous" but still cannot get a print jobs to run successfully.
I need to get http working for this, rather than Samba, as the end game will involve using https.

Any/all help much appreciated.

Regards,

Gavin

---

### Post by SeijiSensei on 2015-04-27
Usually you need to connect to the server's port 631 which is the one assigned for the [Internet Printing Protocol]("http://en.wikipedia.org/wiki/Internet_Printing_Protocol").  CUPS can print directly to an IPP printer if you select that option when [setting up the printer]("http://localhost:631/").  Otherwise try using the URL:
```
 http://server:631/printers
```
I'm not sure you'll be able to use HTTPS for this task.  I saw a couple of articles when searching for "ipp secure," but it sounded like you needed a lot of cruft like printers that have their own SSL certificates included.  I'm pretty sure just adding https: as the protocol will not work on port 631.

---

### Post by dino99 on 2015-04-27
Quite ready to use out of the box  ):P
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by gavinw2 on 2015-04-28
SeijiSensei,

My 'cups server' is a Windows Print Server (Windows 2012), so my URL for the server is 'http://server/printers' or 'https://server/printers'.

---

### Post by gavinw2 on 2015-04-28
Dino99,


I have asked for help getting printing working from an Ubuntu desktop to a Windows server using http and/or https.
The document you have linked to covers only SMB/Samba for that scenario.

Thanks,

Gavin

---

### Post by SeijiSensei on 2015-04-28
From [http://www.techotopia.com/index.php/Setting_Up_a_Windows_Server_2008_Print_Server](http://www.techotopia.com/index.php/Setting_Up_a_Windows_Server_2008_Print_Server)
> 
Internet Printing - Creates an Internet Information Service (IIS) hosted web site where users can manage printers and connect and print to shared printers hosted in the server using the Internet Printing Protocol (IPP). The default URL for the web site is [http://servername/Printers](http://servername/Printers), where servername is the name of the server running the print services.
This sounds to me like two services are created, one using HTTP and one using IPP.  If you install [NMAP](http://www.insecure.org/nmap) with "sudo apt-get install nmap" you can scan the server with "nmap servername" and see what ports are open.  

Try this. Open [http://localhost:631/](http://localhost:631/) on the Ubuntu machine. Delete any existing configurations you might have for the printer.  Now choose Adding Printers and Classes then press the Find New Printers button.  Does CUPS see the printer?  If not, try a manual installation with Add Printer.  Choose "Internet Printing Protocol (http)" and follow the steps provided.  If that doesn't work, use "Internet Printing Protocol (ipp)" instead.

---

