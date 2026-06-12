---
title: "ClamAV not detecting Virus in a specific rar file"
date: 2018-07-25
forum: General Help
---

### Post by drees90 on 2018-07-25
Hi Ubuntu Forum i am new to the pack and hope this is the right point to ask my question :)

Now back to topic i use clamav-postfix on my internal mailserver to check all incoming and outgoing traffic. Generally the virus detection works really well i also installed some of the unofficial signatures which even more so boosted the accuracy. 

Last week we got a mail which contained a scr file inside a rar clamav-milter let it through and saying it's clean. After that the windows security essentials software on one of our clients detected the virus inside the rar package.

I then went to try out why it hasn't been dected (The unrared scr file get's detected easyly by clamav). So i went and tried out some more test-rar files which were provided by clamav and other sources. All got detected and handled the way we wanted to. 

I tried installing all different kinds of signatures even tried to block scr in rar files nothing helped.

I reinstalled clamav from the base package and set up everything again still not able to detect that one specific scr in the rar file.

Maybe someone stumbled across the same problem i could also provide the infected file if wanted

Kind Regards 
Drees

---

### Post by Holger_Gehrke on 2018-07-25
Check whether the compressed file is actually a rar ('file' and or 'mimetype'). It might also be a new version of rar, I recall that they changed the format of rar a while ago (I think it was version 5 of winrar, which at default settings produced files no other program could open).

Holger

---

### Post by drees90 on 2018-07-25
Ty i checked the mime-type it is a normal .rar file. (Not sure about the rar version though any way i can check that?)

---

### Post by Holger_Gehrke on 2018-07-25
That's the reason I mentioned 'file' first, for rar files it gives the version of the file format.

The log of commits at the github repo at [https://github.com/vrtadmin/clamav-devel](https://github.com/vrtadmin/clamav-devel) shows some changes to the unrar code in ClamAV made in June which are in Version 0.100.1. What version are you using ?

Holger

---

### Post by drees90 on 2018-07-26
I am using 0.100.1 we mostly have a update real quick policy on our end so that's not the case here (sadly would be a nice quick solution). 
The rar file version is v37 .
Drees

---

### Post by Holger_Gehrke on 2018-07-26
Well, your ClamAV is current.
v37 ? Really ? Not missing a decimal point in there ? I thought v5.something was current ...
Beyond that, the only idea I have is to report this as a bug and send the rar as a sample to clamav.net.

Holger

---

### Post by drees90 on 2018-07-26
Well i found something maybe thats a hint. The clamconf -n command showed an LDFLAG where '--disable-unrar'  is set. Still wondering since it can unpack other rars just fine.

I gonna file a report over on their site. Ty for your help so far though :)

Drees

---

### Post by SeijiSensei on 2018-07-26
You need a scanner that unpacks archives and scans their payloads.  I use [Mailscanner]("http://www.mailscanner.info/") for this task.

---

