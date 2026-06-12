---
title: "Can I install software on my Palm Tungsten E?"
date: 2007-08-20
forum: General Help
---

### Post by Adski13 on 2007-08-20
Hello Guys,

This is more of a query than a problem at the moment.

I am a relative newbie to the Linux world in general but have done my best to leave the safety (if you can call it that) and the comfort of Windows behind me and make the jump to Ubuntu.  In doing so i have tried to migrate my Palm Tungsten E across too.  It took me an absolute age to get my E to sync with Gnome-Pilot and despite reading the numerous posts managed to get it working by a combination of blind perseverance and luck rather than anything clever.

Anyhoo, now i can get Evolution to sync with my palm i have realised that i have only the most basic apps installed on my E (it was sitting idle in a drawer for so long it has reset itself to factory settings).  My question really is this:

Is it possible to install applications to a palm (obviously in this case a tungsten E) such as pdf viewer, documents to go, Avant go etc. etc. with Ubuntu/Gnome-Pilot (or any other Ubuntu-based software) or do i need to revert to Windows (Boo Hiss) to get my Palm set up initially?

Any help would be great as there seems to be no info anywhere about this!  Many thanks guys!  This forum has been a veritable gold mine for me and has helped me numerous times so far!  Don't fail me now!

---

### Post by UK-Wobbie on 2007-08-20
> **Adski13 said:**
> Hello Guys,

This is more of a query than a problem at the moment.

I am a relative newbie to the Linux world in general but have done my best to leave the safety (if you can call it that) and the comfort of Windows behind me and make the jump to Ubuntu.  In doing so i have tried to migrate my Palm Tungsten E across too.  It took me an absolute age to get my E to sync with Gnome-Pilot and despite reading the numerous posts managed to get it working by a combination of blind perseverance and luck rather than anything clever.

Anyhoo, now i can get Evolution to sync with my palm i have realised that i have only the most basic apps installed on my E (it was sitting idle in a drawer for so long it has reset itself to factory settings).  My question really is this:

Is it possible to install applications to a palm (obviously in this case a tungsten E) such as pdf viewer, documents to go, Avant go etc. etc. with Ubuntu/Gnome-Pilot (or any other Ubuntu-based software) or do i need to revert to Windows (Boo Hiss) to get my Palm set up initially?

Any help would be great as there seems to be no info anywhere about this!  Many thanks guys!  This forum has been a veritable gold mine for me and has helped me numerous times so far!  Don't fail me now!

Hey Adski13.
I have got a Sony Palm and that works ok on Ubuntu  :) All i did is plugged it in and i can look in to My Palm files... Give yours a go!

---

### Post by Adski13 on 2007-08-21
Maybe i wasn't clear before.  

It's not syncing that is causing me problems.  I can sync fine.  It is purely a case of trying to get extra/third party software (such as documents to go, avant go, versamail etc.) which is not installed as standard but i have on the windows install CD, onto my palm.  

As it stands i cannot install anything onto the palm as it appears all the install files are (understandably) .exe files.  Usually on Windows you would use the CD to install the palm desktop which gives you the option to install these apps as part of the initial sync.

Hope this clarifies the issue.

---

### Post by brownrl on 2007-11-07
Any updates on this, I am interested to find out?

We have a Palm Z22 ( simple cheapy palm )

Syncing works and works great.

We now actually use Evolution instead of Thunderbird just for syncing feature.

But as the person before... Is there a way to:

1. Install games, apps, etc

2. Install PiLoc localization for Dutch?


Thanks a ton in advance
Rob

---

### Post by astx813 on 2007-11-26
It's been years since I used a Palm, but now that I have a Centro I'm back in the mix.  I stumbled across this thread while looking for a better way to install apps, and ended up coming up with a better way in the process!  First, enable the File conduit by going to Preferences - PalmOS Devices - Conduits.  Find "File" in the list and click Enable.  Then close that and use the following command line:

```
gpilot-install file <FILE>
or
gpilot-install file --later <FILE>
```

<FILE> is usually a .PRC (palm program) or .PDB (file or database).  The first method will immediately prompt you to press the Hotsync button.  If you use --later, you can queue up multiple files so you won't have to sync repeatedly.  They'll all be copied over on the next sync,  

In fact, I guess this can be made pretty easy.  After you enable the File conduit, right click on a file you want to put on your palm (a .PRC or .PDB) and select Open With Other Application...  Click the arrow to expand "Use a custom command" and type "gpilot-install-file --later" (leave off the --later to sync immediately) and click OK.  Now, whenever you double-click on a prc, it'll be set to upload on the next hotsync.

I don't love this method (no visual confirmation, not sure how to remove a file from the queue if you change your mind), but it gets the job done.

---

### Post by tramir on 2007-12-15
Just found this thread, saved my life! A couple of corrections, though:

1. In Gutsy, the application for queuing files is called gpilot-install-file (instead of gpilot-install file).

2. You can get the visual confirmation of having installed the files in two ways:
(i) Use gpilot-install-file --later <PRC or PDB filename>, and then use the Gnome Pilot Applet (which will show in a window each action performed, including each file installed).
(ii) Less nice: check the log file on the PDA after the hot-sync :)

I still couldn't figure out how to delete files from the queue, but at least we can install stuff on the PDA!

Cheers,
Mircea

---

### Post by Sims2789 on 2007-12-17
Is there a GUI for this command line method? How do I install files to the flash card as opposed to the Palm's memory itself?

---

### Post by wahoobob on 2007-12-18
How can we put Mp3's etc on our palm - esp. in the card?

---

### Post by astx813 on 2007-12-20
Wahoobob: The easiest way I've found to put files directly onto the memory card is a tool called Softick Card Export.  It's not free, but it's worth taking a glance at.  It's kinda neat, run the app and connect to your PC and it'll turn your palm into a card reader.  Make it snappy, though, while it's acting like the card reader, it's NOT acting like a phone.

---

### Post by niteshifter on 2007-12-20
> How can we put Mp3's etc on our palm - esp. in the card? 

Depends on the unit (E, C series, TX, etc.) - some don't present the card as a USB MSC device, some do. Some can with third party software.

Universal solution - for about $15 get a multi-card reader. Connects to PC via USB and whatever card inserted appears and acts like an ordinary USB thumb drive.

---

### Post by Sims2789 on 2007-12-21
> **niteshifter said:**
> Depends on the unit (E, C series, TX, etc.) - some don't present the card as a USB MSC device, some do. Some can with third party software.

Universal solution - for about $15 get a multi-card reader. Connects to PC via USB and whatever card inserted appears and acts like an ordinary USB thumb drive.

I have a built-in card reader and when I insert SD cards it detects them as SD cards, not as USB drives, so I just manually add files like I do to my USB card. However, I still don't know how to install programs onto the card itself, nor do I know how to use the GUI to install programs to the Treo's main memory.

---

### Post by bgoody on 2007-12-24
Hi.  There is a Linux program called J-pilot which is almost a duplicate of the Palm Windows software. It's in Synaptic. It can be used to  install programs into your Palm.

The option is under the  File menu.

BTW, to sync with J-pilot hit the Hotsync button on your Palm FIRST then the sync button in J-Pilot.

---

### Post by Timokl on 2008-02-21
> **tramir said:**
> Just found this thread, saved my life! A couple of corrections, though:

Yes, thanks from me, too.

:popcorn:

Timo

---

