---
title: "[SOLVED] Browser issue - downloading scientific journals"
date: 2007-10-17
forum: General Help
---

### Post by rax_m on 2007-10-17
Hi 

I am having issues with downloading scientific journals (PDFs) in Linux from home (I tried firefox and opera). 
Basically, in order to go to a journal site I have to go "through" the university library site that links me to all the journal publishers. I can search etc. but when I try and download an article it sometimes just dies halfway or very close to the beginning of the download. 

The problem is this does not happen EVERY time.. in some cases I can successfully download something. 

This issue also sometimes happens to me in yahoo mail when trying to download attachments. I find its more successful when I download using "open with ..." rather than "save to disk". Don't ask me how this can make any sense!

Oh.. and I forgot to mention that the speed is ridiculously slow (specifically for the journals). I don't have this issue with other downloads. 

I know it's not a general network issue because  I can download it successfully from a Windows XP computer connected to the same network within a minute. 

PLEASE HELP! :confused:

Thanks 
Rax

---

### Post by rax_m on 2007-10-18
bump

---

### Post by rax_m on 2007-10-20
another *bump*

---

### Post by Can+~ on 2007-10-20
Are you connected via wifi? Only PDFs? Can we see one of those pdf's? Add more info if you want help ;D.

---

### Post by Arrdee on 2007-10-20
Also, are you using Adobe Reader? Just would be useful to know.

---

### Post by rax_m on 2007-10-21
Hi Can+, Ardee

Thanks for the replies.. 

It only seems to happen with PDFs and in particular only when I go through my university site to the scientific journal sites (like [www.sciencedirect.com](www.sciencedirect.com)). I have to go thru the unversity site as they are the ones who pay the subscription to the journal sites.

I'm using eVince document viewer.. but maybe I'll try and install Acrobat now. I am using Acrobat on the Windows machine. 

I've tried to attach an  example of the PDF.. but the forum limits the upload size to 20KB.. These are  in the region of 0.5MB and larger.. 

Yep. I am connected through WiFi.. though this doesn't seem to make any difference when downloading attachments from other sites. Maybe I'll try connecting directy to the modem and see if that makes any difference. 

Firefox on a WinXP machine on the same network (but a wired connection) doesn't have this issue.

It can't be the router.. as I've just put in a new one yesterday (other one got blown by lightning :( ) 

Hope you guys can help shed some light :) 

Thanks again

---

### Post by dcstar on 2007-10-21
> **rax_m said:**
> Hi Can+, Ardee

Thanks for the replies.. 

It only seems to happen with PDFs and in particular only when I go through my university site to the scientific journal sites (like [www.sciencedirect.com](www.sciencedirect.com)). I have to go thru the unversity site as they are the ones who pay the subscription to the journal sites.
..........
Firefox on a WinXP machine on the same network (but a wired connection) doesn't have this issue.

It can't be the router.. as I've just put in a new one yesterday (other one got blown by lightning :( ) 

Hope you guys can help shed some light :) 

Thanks again

I believe some Universities are using IPv6, so your Ubuntu may be attempting to use this protocol when perhaps it isn't fully operational yet.

Do a forum search for "disable IPv6", the solutions may be of use.

---

### Post by legatek on 2007-10-21
Are you trying to save to a NTFS-formatted partition? I have problems downloading large files to NTFS, they usually complete but are almost always corrupted. I solved this issue by setting up a download folder on a ext3 or FAT-formatted drive and later moving to the NTFS partition if necessary.

---

### Post by rax_m on 2007-10-21
Hi all .. 

Well.. I did some experimenting... 
It seems that having Adobe acrobat installed and letting the journal sites open the link embedded into firefox allows *most* of the journals to download successfully. 

legatek - I have tried downloading to both ext3 and NTFS (but mostly to NTFS). 

dcstar - I'll look into disabling IPV6 and see if that makes any difference

I'll do some checks and let you know what the status is ... and then mark this as (kindof) fixed later. 

Thanks loads for the replies .. 

Rax

---

### Post by rax_m on 2007-10-21
Ok.. I disabled IPV6 .. not sure I can see a speed improvement, but my journals are definitely downloading now. 

My gut feel is that Adobe may use some kind of download protocol that allows it to display some of the document while still downloading the rest. The websites may be tied into this protocol some how. 

Thanks for the help everyone! 
Rax

---

