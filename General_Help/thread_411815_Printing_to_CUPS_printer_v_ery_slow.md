---
title: "Printing to CUPS printer v ery slow"
date: 2007-04-17
forum: General Help
---

### Post by acormack on 2007-04-17
I am using Kubuntu Edgy to print via CUPS to TCP/IP connected printer (Ricoh Aficio MP C4500 PXL)

The print quality is great and all the features of the printer are supported!

My problem is that printing is very slow.  There is a delay of perhaps 30+ seconds before any sheet is printed then a delay of about 10-15 seconds between each sheet.

If I print to the same printer via a samba share it prints very fast with no delays.  Does anyone have any idea why CUPS is slow please?

Thanks in advance


Alec

---

### Post by boast on 2007-05-11
same here

---

### Post by theDentist on 2007-05-15
I posted just a day ago about printing. Me too, when I print photos using CUPS, it takes 30 minutes to print a 6" x 4" print of high quality, in windows it takes only a few minutes.  It must be something about CUPS. I even installed the GIMP plugin for cups which I'm afraid made no difference, Any Ideas!!!       :mad:

---

### Post by ironslave on 2007-05-15
i also have this problem with slow startup times... 30+seconds, and i am running an HP laserjet printer

---

### Post by eggert on 2007-05-20
I've also got a problem with slow printing, though maybe it is not the same issue.
If I try to print large jobs from any KDE program using kprinter, cups takes a very long time finishing the job.
For testing I created a one page document in KWord containing two 3 mpix images.  Printing it created in a few seconds a 20 MB job in CUPS which then started right away sending data to the printer (led started flashing) and kept on doing that for 14 minutes when it finally printed.  The exact same document from Open office writer was a 22 Mb job which finished in under a minute.
This test was done with fully updated Kubuntu Feisty and Lexmark C720 network printer, but I have made many tests with 3 computers (2x Kubuntu Feisty, 1x FC5 w/KDE) and 3 different printers (2x Lexmark, 1x RICOH all network connected) and many programs, f.ex. 1 image from GIMP in a few seconds but Krita took 7 minutes printing one image.  Setting kprinter to print to file and then printing that file with, lpr -P LexmarkC720 also took this long time.
My conclusion for this is that CUPS is not slow at all but the ps file kreated by kprinter is in some way strange, which results in this very long time for printing.

So, I have no help to offer but maybe if someone more experienced reads this they can assist.

Cheers,
Eggert

---

### Post by OZSYD on 2007-05-24
I have a Canon LBP1120 and the printing speed is very slow. Someone told me that this is because I am using a Postscript system which is not native for my printer. Does anyone know  a non-postscript driver for this printer to use with UBUNTU?

---

### Post by lord_alan on 2007-05-24
Hi all,

I have a similar problem to others on this thread.

My setup is Ubuntu 7.04 (desktop normal 32bit) on an AMD 64 3200+ with a gig of DDR Ram. I have two printers: 
[LIST]
[*]A monochrome HP LaserJet 6L connected on LPT1,
[/LIST]
[LIST]
[*]A Konica Minolta 2530DL Network attached colour laser printer.
[/LIST]

The HP Laserjet printer is fine all the time.

The 2530DL works fine "most of the time" but sometimes the printer will take an "age (30mins+) to print something. Opening the print queue and looking at the printer properties gives me messages such as - network host busy trying again in 30secs, or the job might be printing but the percentage complete sits at odd figures like 36% for ages.

Repeatedly opening and closing the printer queue and pausing and resuming things doesn't seem to make much difference. It is this end that is the problem, the print job is not being sent to the printer, it's not that the printer is taking an age to process the job itself.

The weird thing is, that once the printer bursts into life, all subsequent jobs are fine... for a while at least.

Anyone got any good ideas?

Cheers

Al

---

### Post by zindine on 2007-11-01
I don't know the answer to your problem, but I would be curious to know how you configured the Ricoh printer to print over TCP/IP. 

What protocol did you use and so on... 

Thanks 

Zindine

---

### Post by gilf on 2007-12-07
Similar problem here with a Canon S600. Very long printing times when compared with Windows.

Is this just a thread to note the fact or is someone going to actually propose a solution, or procedure???  I've searched for many threads in this forum on slow printing and haven't yet found a solution.

Specifics:

I'm using Ubuntu Gutsy 7.10 printing via Samba to a shared printer. Test page prints fine, but slowly.

Using CUPS and driver:

Canon S600 Foomatic/bj8pa06n.upp (recommended)

So what do I do, go back to windows over this simple but critical issue?

23,000 available Linux programs are nice, but most of them need to print.

---

### Post by acormack on 2007-12-08
gilf

When you say you are printing via Samba do you mean that the print queue is defined on a windows box somewhere?

What happens if you print to the printer direct to its IP address?  Is it still slow?

---

### Post by gilf on 2007-12-11
Thanks ackoramck for helping! 

Sorry about the frustrated tone earlier..

I was using a device url of //smb...etc though the printer share machine is actually a Ubuntu machine. In other words I am using a samba network (because other windows machines need to access this printer.)

The machine I was trying to print from when I had a problem happened to be another Ubuntu machine. So it was two ubuntu machines communicating over samba.

I don't think the fact that the Ubuntu machines are using Samba to print should be a problem. In fact I know it isn't, because I have since resolved the issue and the print speed is fine using samba.

The issue turned out to be the (recommended) foomatic driver for the Canon S600, listed above. When I went to CUIPS and switched over to the Guttenprint driver for the S600,  the print speed seemed fine.

I noticed a more specific characteristic of the Foomatic driver problem FYI and for others who may also have problems:  that is, I believe the printer was loaded after the job was spooled, but never seemed to actually print. The printer busy light would flash, then stop, but the print head would not move.

I came across a reference somewhere else (can't find it now) that a Foomatic driver was not sending an EOF character, and that this could be changed in a setting. If the Canon S600 needs an EOF to print, perhaps this is the problem.

 Because I got the Guttenprint driver working, I didn't investigate this possibility further, but it would be worth knowing about in case others have a similar problem with this or other printers where an alternative Guttenprint driver wasn'a available.

Thanks again for taking the time to help ackormack, I appreciate it!

---

### Post by redsun82 on 2007-12-26
Hi, I also have an issue with slow TCP/IP printing.

I have a Canon MP150 connected to an airport express. Using Gutenprint CUPS driver, raw TCP/socket. The printing starts like a charm, practically immediately, and prints at normal speed. Then, either a little before the end of the document or after more or less 8 pages, *whichever comes first*,it stops and begins to print a single line every 10 seconds or so. Very unnerving. Other machines running windows print alright.

I hope more people start to show up on this post lending a hand...

---

### Post by trycage on 2008-04-15
The same here

I have a brother 7820N connected through network.
The Br-Script-3 driver is very slow. Using standard postscript driver improved the speed a little better
 but a 20Mbyte (10 pages) job took at least 5 minutes to be printed. 
The printer print at normal speed under Windows and even under MacOsX . 
My OS  is Ubuntu 7.10

Thanks

Trycage

---

