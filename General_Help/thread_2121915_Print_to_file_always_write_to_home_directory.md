---
title: "Print to file always write to home directory"
date: 2013-03-03
forum: General Help
---

### Post by Wykzl on 2013-03-03
Hi,

I'm using ubuntu 12.10 and latelly I've noticed that when I print to file, the output always goes to hoem directory, even if I choose a subdirectory (Documents, for instance).
I've been printing to Documents for a long time, so something is different at this version.
Also I'm not sure if I ever printed correctly with 12.10, but quite sure that did it before.
I'm using the 64bits version.

Anyone knows how to "covince" ubuntu to use the directory I choose instead home ?

(btw...noticed that System Settings->Details says I'm using ubuntu 13.04... but lsb_release -a says 12.10)

---

### Post by Bufeu on 2013-03-03
13.04 isn't even releases. As the name says, 13.04 will be released in April (20**13**-**04**), in other words, next month.

---

### Post by Kevin McCready on 2013-03-12
bump
I also need to print to file when I have no "ink printer" attached. How can I fool my system into doing this?

---

### Post by kurt18947 on 2013-03-12
> **Kevin McCready said:**
> bump
I also need to print to file when I have no "ink printer" attached. How can I fool my system into doing this?

You should not have to fool anything.  The "printer" should be installed as part of the initial installation process.  I have no physical on this install.  I'm using Firefox.  Click 'file' -> 'print' -> 'print to file'.  Change to file name from 'mozilla.pdf' to something_else .pdf, select .pdf or .ps and select a destination folder. Click 'print'.

---

### Post by Kevin McCready on 2013-03-12
No that doesn't work. I'm printing from within an app running in firefox. The ap insists on a physical printer being connected. So I DO need to convince my system that there is a physical printer connected.

---

### Post by kurt18947 on 2013-03-12
> **Kevin McCready said:**
> No that doesn't work. I'm printing from within an app running in firefox. The ap insists on a physical printer being connected. So I DO need to convince my system that there is a physical printer connected.

Ah.  There's a coupon printer - only works in Windows - like that. It would not print to a virtual printer like cutepdf.  I'd guess it only 'talks' to a port like LPT or USB but have no real knowledge on the subject.

---

### Post by albandy on 2013-03-12
sudo apt-get install cups-pdf
then go to cups administration page: [http://localhost:631](http://localhost:631)
Go to administration --> add printer
Select "CUPS-PDF (virtual PDF printer) and press "next"
Set the printer name as you want and press "next"
Then in the printer vendor list select generic and press "next"
Now select Generic CUPS-PDF Printer and press "add printer"
Change the printer resolution as you want and press "change default options"

Then print in your new pdf printer. All pdf's will be saved in your home  inside PDF folder

---

### Post by Kevin McCready on 2013-03-12
Thanks
Managed to install.
The system says it's printed.
Can't find the file or folder.
Tried
locate pdf >t
leafpad t
searched for virtual, searched for lots of things, no luck

---

### Post by Wykzl on 2013-03-12
> **kurt18947 said:**
> You should not have to fool anything.  The "printer" should be installed as part of the initial installation process.  I have no physical on this install.  I'm using Firefox.  Click 'file' -> 'print' -> 'print to file'.  Change to file name from 'mozilla.pdf' to something_else .pdf, select .pdf or .ps and select a destination folder. Click 'print'.

When you select a destination folder, the file actually goes to there ?
Up to 12.10 I had no problem with that. Now it always goes to home directory, no matter what destination folder I select.

Any help ?

---

### Post by plucky on 2013-03-12
> **Wykzl said:**
> When you select a destination folder, the file actually goes to there ?
Up to 12.10 I had no problem with that. Now it always goes to home directory, no matter what destination folder I select.

Any help ?

13.04 is still in development.

If you want it fixed before official release,I would suggest logging a bug report on Launchpad.


Good Luck

---

### Post by Kevin McCready on 2013-03-12
v

---

### Post by Kevin McCready on 2013-03-12
Right now I don't mind where it saves to. The virtural-pdf printer says it's printed a file. But I can't find it anywhere. here's what's written inside /etc/cups/printers.conf:
<Printer Virtual_PDF_Printer>
UUID urn:uuid:5dc850c1-d1a6-3095-5ac7-962019804a05
Info Virtual PDF Printer
Location 
MakeModel Generic CUPS-PDF Printer
DeviceURI cups-pdf:/
State Idle
StateTime 1363121286
Type 8450124
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

If anyone can help find the "printed" pdf's that would be great. Or figure out why it hasn't printed when it says it has.

---

### Post by schragge on 2013-03-12
Maybe there's something in CUPS logs */var/log/cups/* or in CUPS web interface [http://localhost:631](http://localhost:631)

---

### Post by Kevin McCready on 2013-03-12
Thanks for you reply. I checked the logs and found the test print page but nothing else in:
/var/spool/cups-pdf/ANONYMOUS

When I tried to print from firefox, rather than the app within firefox, the virtual printer had a message which said:
usr/lib/cups/filter/commandtops failed

but I don't have a /usr/lib/cups  directory

When I checked the error_log there were heaps of dbus errors, filter errors etc etc.

hmmm, time to give up on cups?

---

### Post by bab1 on 2013-03-13
All print to PDF files are by default sent to ~/PDF ( that is /home/$USER/PDF).  This is configured and monitored in AppAmour, the security module for the Linux kernel.  You as a user can't redirect the saving of the file or directly change the configuration settings in CUPS-PDF.  You need to also configure AppAmour or turn it off.  To my way of thinking this is a PITA for such a little thing.  I usually make a sym-link to the Desktop and rename and move the file to where I want it later.

In a nutshell, look in the PDF directory in you home directory for the files you are printing to CUPS-PDF.

---

### Post by albandy on 2013-03-13
> **Kevin McCready said:**
> Thanks
Managed to install.
The system says it's printed.
Can't find the file or folder.
Tried
locate pdf >t
leafpad t
searched for virtual, searched for lots of things, no luck

Check this video:
[http://youtu.be/R_cgpMGNJck](http://youtu.be/R_cgpMGNJck)

---

### Post by Kevin McCready on 2013-03-13
Thanks, but that doesn't solve the problem. The problem is that within the app which runs within firefox, the cups system doesn't work. It generates all the errors I referred to above.

---

### Post by albandy on 2013-03-13
> **Kevin McCready said:**
> Thanks, but that doesn't solve the problem. The problem is that within the app which runs within firefox, the cups system doesn't work. It generates all the errors I referred to above.

Is this application public available? Can I download it to make some tests?

---

### Post by Kevin McCready on 2013-03-13
here it is here:

[http://np.netpublicator.com/netpublication/n75088268](http://np.netpublicator.com/netpublication/n75088268)

---

### Post by albandy on 2013-03-13
> **Kevin McCready said:**
> here it is here:

[http://np.netpublicator.com/netpublication/n75088268](http://np.netpublicator.com/netpublication/n75088268)

It worked for me with 12.04, now I will test it with 13.04

---

### Post by Kevin McCready on 2013-03-13
You mean you could save a copy to your home directory? Not print a hard copy.

---

### Post by albandy on 2013-03-13
I've pressed the print button and cups printed as pdf the page displayed.

[ATTACH=CONFIG]240115[/ATTACH]

---

### Post by Kevin McCready on 2013-03-13
The print button in the app or the print button via firefox? Can you save the whole thing?

---

### Post by albandy on 2013-03-13
> **Kevin McCready said:**
> The print button in the app or the print button via firefox? Can you save the whole thing?

The print button in the app, but I only can print the page displayed.

---

