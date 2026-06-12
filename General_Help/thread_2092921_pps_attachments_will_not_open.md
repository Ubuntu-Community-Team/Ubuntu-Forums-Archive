---
title: "pps attachments will not open"
date: 2012-12-09
forum: General Help
---

### Post by kimberley on 2012-12-09
Since updating to 12.4 I have not been able to open pps email attachments. I have searched all 'help' articles without success.  One forum entry says Libre Office opens these files automatically. Can someone please tell me what  I need to do.

---

### Post by TheFu on 2012-12-09
PPS attachments are usually filled with viruses, so I avoid opening them at all, even on Linux.
However, if you are certain that you need to open the attachment, the LibreOffice powerpoint clone, Impress, is needed to open it.  I'd open synaptic with a **sudo synaptic**, then type in **impress** into the search field and install it. The package you want to install is named "**libreoffice-impress**" on my system.

If opening the file directly from the email program is not working, you may want to save the file under /tmp and manually open it either by using the GUI to click on it or from a shell with **libreoffice /tmp/file.pps** where the file.pps is the filename you selected at download.

---

### Post by Kirk Schnable on 2012-12-09
> **TheFu said:**
> PPS attachments are usually filled with viruses, so I avoid opening them at all, even on Linux.

Did I miss a meeting?   PPS files are PowerPoint Viewer files. As far as I'm aware, the only way to get a virus from Microsoft Office files is if they contain malicious VB code, which won't even run in LibreOffice.  I wouldn't worry about that. 

@Kimberley: You should be able to install LibreOffice from the Software Center if you don't already have it. If you have LibreOffice Impress installed,  try opening your PPS file from the File>Open menu.  If that works, it will be a simple matter to make LibreOffice Impress your default program for opening PPS files.

---

### Post by Merrattic on 2012-12-09
Yes, but Libre Office doesn't ship with XUBUNTU.

One has to install it from the repos.

If the OP already has Libre Office installed this is likely to be a file association issue.

---

### Post by TheFu on 2012-12-09
> **Kirk Schnable said:**
> If you type LibreOffice into the Unity launcher, do you have the option to launch Impress?  If so, open Impress and try opening your PPS file from the File>Open menu.  If that works, it will be a simple matter to make LibreOffice Impress your default program for opening PPS files.
Xubuntu doesn't have Unity - hence the pointer to **Synaptic**.  I could have simply said:
$ sudo apt-get update && sudo apt-get install libreoffice-impress*
but I was trying to be more GUI-user friendly.

Software Center is missing thousands of apps in the attempt for "simplicity", so I didn't want to suggest looking in there if I didn't know the package existed.  I checked inside Synaptic, it had it.

MS-Office documents all have "undocumented features" - also called bugs. At some point support for javascript was added which IS supported in OO and LO. 

I've never seen a PPS file that did not contain a virus myself.  Perhaps my experiences have been on the extreme edge?  I dunno.  Best to be cautious with any MS or Adobe attachments, IMHO.

Anyway - hopefully this answers "why" I suggested things in a certain way. Others clearly have a different opinion.  Seeing the different opinions is a good thing, right?

---

### Post by Kirk Schnable on 2012-12-09
> **TheFu said:**
> Xubuntu doesn't have Unity - hence the pointer to **Synaptic**.

My bad, I saw 12.04 in the thread, and I neglected to notice the Xubuntu tag on the thread.  Sorry about that.

---

### Post by kimberley on 2012-12-11
> **Kirk Schnable said:**
> Did I miss a meeting?   PPS files are PowerPoint Viewer files. As far as I'm aware, the only way to get a virus from Microsoft Office files is if they contain malicious VB code, which won't even run in LibreOffice.  I wouldn't worry about that. 

@Kimberley: You should be able to install LibreOffice from the Software Center if you don't already have it. If you have LibreOffice Impress installed,  try opening your PPS file from the File>Open menu.  If that works, it will be a simple matter to make LibreOffice Impress your default program for opening PPS files.

Thank you all for your prompt responses. I omitted to say that I  have Libre Office Writer 3 installed and have tried to open pps files  From File-Open Menu but without success.  Should I download Libre Office Impress to open these filese - I cannot find it in the software centre.

---

### Post by TheFu on 2012-12-11
> **kimberley said:**
> Thank you all for your prompt responses. I omitted to say that I  have Libre Office Writer 3 installed and have tried to open pps files  From File-Open Menu but without success.  Should I download Libre Office Impress to open these filese - I cannot find it in the software centre.
Which is why I suggested that you use **Synaptic** - Software Center doesn't show all the software available.  You many need to install Synaptic first. It is the pre-12.04 package GUI.

Or you could run that little script I spelled out earlier. That would be easier, but you may not be comfortable at a shell/terminal prompt.

---

### Post by Kirk Schnable on 2012-12-13
> **kimberley said:**
> Thank you all for your prompt responses. I omitted to say that I  have Libre Office Writer 3 installed and have tried to open pps files  From File-Open Menu but without success.  Should I download Libre Office Impress to open these filese [...]

Yep.  Opening a PPS file with LibreOffice Writer is like trying to open a PowerPoint with Microsoft Word.  

You will be needing LibreOffice Impress.  

Here's some information on how to use Synaptic (TheFu's suggested method)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

And if you still need assistance, here's the broader "how to install software on Ubuntu" help topic.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by kimberley on 2012-12-14
Hi, thank you Kirk and The Fu. I now have Libre Office Impress after using Synaptic Package Manager - a first for me. However, I was expecting the pps doc email attachment to open automatically which is doesn't, nor have I been able to open it by saving and launching Impress - obviously something is still not quite right or I am doing something wrong? 

Although pps email attchments still do not open automatically using Libre Impress,  I can now view the files by copying and pasting into 'documents' and viewing with Impress. Obviously didn't do it right on first try.  There is probably a quicker way but at least this works.

---

### Post by bryncoles on 2012-12-14
Hi kimberley

Forgive me for asking the obvious, but have you tried right-clicking the pps file and selecting 'open with libreoffice impress'?

---

### Post by TheFu on 2012-12-14
> **bryncoles said:**
> Hi kimberley

Forgive me for asking the obvious, but have you tried right-clicking the pps file and selecting 'open with libreoffice impress'?

You may need to restart the app that you hope will open the attachment too, so it will re-read altered initial settings.  So, have you restarted your email program or the file browser?  Sometimes a logout and login is the easiest way - no need to reboot.

---

### Post by kimberley on 2012-12-17
[SIZE=3]How dumb am I!!  Yes, a right click solved the problem after downloading Libre Impress.
A big thanks to all who responded to my problem.[/SIZE]:p

---

