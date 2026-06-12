---
title: "Gutsy: Where do cups-pdf print jobs go?"
date: 2007-10-21
forum: General Help
---

### Post by DavidTangye on 2007-10-21
When I print jobs to the cups-pdf printer queue in Gutsy, , even though its spool job record appears in /var/spool/cups, I cannot find the pdf file that should be produced. I even tried to 'find / -mmin -1 -name "*pfd"' and "*PDF".

Before Gutsy, the cups-pdf package set up cups-pdf print jobs to go to $HOME/PDF. This is still the default that is set in /etc/cups/cups-pdf.conf for Gutsy
> Out ${HOME}/PDFHowever in Gutsy the printer configuration, as seen in the Admin utility or web browser at localhost:631 shows
```
Device URI: cups-pdf:/
```I wonder if this is incorrect.

I can print a test page from either interface. The output appears at /var/spool/cups-pdf/ANONYMOUS/Test_Page.pdf. I just cant find the output of a normal job.

Ideas, anyone?

---

### Post by mahousaru on 2007-10-21
The device URI is also cups-pdf:/, but mine works.  I haven't tried to change the out location in cups-pdf.conf so I don't know if that works.

Have you tried to re-create the device?   Make sure the cups-pdf.conf has been renamed to something else once you delete the old pdf printer device

---

### Post by LanDan on 2007-10-21
your settngs seem correct and identical to mine

they should appear in your home folder in a folder called PDF

anything strange in your /var/log/cups/access.log ?

---

### Post by DavidTangye on 2007-10-21
I just did an upgrade of a standard Feisty installation to Gutsy. I have deliberately not hacked anything at all, so I hoped to have the upgrade work perfectly, and not now have to start hacking anything.

Just wondering: What does your 'Out' line in cups-pdf.conf say?

---

### Post by LanDan on 2007-10-21
same as yours,

the settings itself are correct, 
you have the cups-pdf package installed?

---

### Post by DavidTangye on 2007-10-21
No. The last lines look fine:
> localhost - - [22/Oct/2007:12:36:08 +1000] "POST / HTTP/1.1" 200 414 CUPS-Get-Classes successful-ok
localhost - - [22/Oct/2007:12:36:09 +1000] "POST / HTTP/1.1" 200 414 CUPS-Get-Classes successful-ok
localhost - - [22/Oct/2007:12:36:09 +1000] "POST /printers/PostScript HTTP/1.1" 200 244695 Print-Job successful-ok
localhost - - [22/Oct/2007:12:36:09 +1000] "POST / HTTP/1.1" 200 176 Get-Jobs successful-ok
localhost - - [22/Oct/2007:12:36:10 +1000] "POST / HTTP/1.1" 200 176 Get-Jobs successful-ok

---

### Post by LanDan on 2007-10-21
then i'm stuck ;)

still might try to look where it ends up

updatedb
locate .pdf

---

### Post by DavidTangye on 2007-10-21
Thanks for your help folks.

I think that I  have found the problem. It appears that under this latest version of cups, $HOME/PDF cannot be a link to a directory. This seems to be a minor bug.

---

### Post by LanDan on 2007-10-21
cool

---

### Post by DavidTangye on 2007-10-21
Dan, Can you confirm this. Make PDF a link: Something like ```
mv PDF PDFz; ln -s PDFz PDF
```

Thanks for your help.

---

### Post by LanDan on 2007-10-21
yup,

the symlink doesn't work

---

### Post by DavidTangye on 2007-10-21
Um yes... its a symlink problem. This used to work with Feisty.. It seems to be a bug.

---

### Post by LanDan on 2007-10-21
you might as well put it on launchpad

---

### Post by zerodamage on 2007-10-22
> **LanDan said:**
> you might as well put it on launchpad

I had the same problem and I did a reinstall of cups-pdf via Synaptic. I am now seeing the missing folder with my files.

---

### Post by stefangachter on 2007-10-23
I have the same problem, but re-installation of cups-pdf via apt-get did not solve it. Anybody has some further ideas? Thanks.

---

### Post by stefangachter on 2007-10-24
I found the solution:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551)

Apparently, some access rights has to be set properly....

And do not use the "Print Test Page" button, because it won't work. Try to print from an application like firefox. This is some joke of ubuntu, having a printer interface with test page button that doesn't work, because it does not consider the current CUPS configuration.

---

### Post by noynac on 2007-10-30
I tried to change the output directory to '~/autosave' from '~/PDF' by changing the /etc/apparmor.d/usr.sbin.cupsd and /etc/cups/cups-pdf.conf files and rebooting. A PDF file is not created and the kernel log shows the following:

Oct 30 11:53:47 dell kernel: [  341.940275] audit(1193770427.334:10):  type=1503 operation="capable" name="dac_override" pid=5609 profile="/usr/lib/cups/backend/cups-pdf"

Oct 30 11:53:47 dell kernel: [  341.940285] audit(1193770427.334:11):  type=1503 operation="capable" name="dac_read_search" pid=5609 profile="/usr/lib/cups/backend/cups-pdf"

Oct 30 11:53:47 dell kernel: [  342.013681] audit(1193770427.334:12):  type=1503 operation="inode_create" requested_mask="w" denied_mask="w" name="/home/bob/autosave/job_779-My_Excite.pdf" pid=5612 profile="/usr/lib/cups/backend/cups-pdf"

I was able to change the output directory in Feisty, and I am able to print to a PDF file in Gutsy if I leave the output directory at '~/PDF'. Anyone have any idea what I need to do to get this to work.  I reinstalled the PDF printer driver, but this didn't help.

Thanks!

---

### Post by agapito on 2007-11-04
That's strange...  :confused:  I did exactly that and I'm able to print to pdf to the new directory (~/Desktop).

---

### Post by noynac on 2007-11-04
> **agapito said:**
> That's strange...  :confused:  I did exactly that and I'm able to print to pdf to the new directory (~/Desktop).

I upgraded from Dapper to Feisty to Gutsy. Perhaps something is gunked up from one of the old installs.

The pertinent portion of the error message seems to be:

requested_mask="w" denied_mask="w" name="/home/bob/autosave/job_779-My_Excite.pdf"

I have no idea what a mask is or why it would be denied. I've adapted to use of the PDF directory for PDF files, so I guess it doesn't matter all that much.

Thanks for the reply.

---

