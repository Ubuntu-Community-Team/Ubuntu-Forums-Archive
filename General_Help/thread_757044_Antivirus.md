---
title: "Antivirus?"
date: 2008-04-16
forum: General Help
---

### Post by seeker1458 on 2008-04-16
Hey guys, got a windows question, but I figured you guys would probably be the best source of information.  I am a Network Admin, and am looking for a decent free real-time/on-access AV. We've got about 60 Presalesmen that spend very little time online, but I would feel more comfortable with some protection.  We use Symantec Endpoint for the rest of the staff...but the overhead required for Endpoint strains our little Fujitsu's. I have used AVAST! in the past but I don't want to violate any EULAs by using it in a business setting.  Any of you know of one that is protected by GPL?

---

### Post by eXtreem on 2008-04-16
Maybe clamwin??

[http://www.clamwin.com/](http://www.clamwin.com/)

It's free, but I don't know if it has a on access scan in it, but you could try..

eXtreem

---

### Post by Achtung on 2008-04-16
Clam AV : [http://www.clamav.net/](http://www.clamav.net/)

---

### Post by seeker1458 on 2008-04-16
From what I have read neither of them have a real time scanner.  I have looked at Moon Secure AV, but people seem to be reporting a good deal of failures with it.

---

### Post by seeker1458 on 2008-04-16
> **Achtung said:**
> Clam AV : [http://www.clamav.net/](http://www.clamav.net/)

Thought ClamAV was for unix only? Isn't ClamWIN the version for microsquish?

---

### Post by Achtung on 2008-04-16
Oops. The clam AV website clearly says on-access scanning is available for linux and BSD only. Sorry!

> **seeker1458 said:**
> Thought ClamAV was for unix only? Isn't ClamWIN the version for microsquish?
I'm not sure whether there's a difference between ClamWin and the Clam AV for Windows package, but they point to different websites for download. 

I haven't used a virus scanner in quite some time now, sorry I can't be of more help.

---

### Post by seeker1458 on 2008-04-16
I just tried installing the Win32 version on ClamAV, and nothing happened.  Brought up the .msi installer and it finished.  Then nothing.  No gui, just an entry in add/remove programs.  I'll try ClamWin...looks like you can schedule scans, so I'll just have it run like once a day M-F.  Maybe that'll work?

---

### Post by eXtreem on 2008-04-16
> Winpooch is open source protection from spyware and the like. By scanning files in real-time on your computer, it detects any malware and makes sure they do not infiltrate your system. Together with ClamWin anti-virus program it even protects your PC from virus by adding the real-time scanning capability that ClamWin lacks. Winpooch sees and prevents all attacks from viruses, spyware, trojan programs, etc.

It looks like if you install clamwin together with winpooch you have a realtime virusscan...

winpooch you can find here: [http://winpooch.free.fr/page/home.php?lang=en&page=home](http://winpooch.free.fr/page/home.php?lang=en&page=home)

---

### Post by ibuclaw on 2008-04-16
I was about to say where is the EULA, but then I found it [here]("http://www.avast.com/eng/free_software.html") and for linux [here]("http://www.avast.com/eng/avast-for-linux-workstation.html").
> 
This software is designed exclusively for home users and non-commercial use.
...
...
Institutions (even non-commercial ones) are not allowed to use avast! **[INSERT YOUR FAVOURITE OS]** Home Edition.


For Windows, there are such software as:
[AntiVir]("http://www.free-av.com/")
[AVG AntiVirus]("http://free.grisoft.com/")
[BitDefender]("http://www.bitdefender.com/")

But freeware only tends to scan half the pack of viruses.
So other spyware/adware apps may be found in this list.
[MS Defender]("http://www.microsoft.com/downloads/details.aspx?FamilyID=435bfce7-da2b-4a6a-afa4-f7f14e605a0d")
[Spyware Terminator]("http://www.spywareterminator.com/")
[Spyware Doctor Starter Edition.]("http://www.pctools.com/spyware-doctor/google_pack/")
[Windows MRT.exe]("http://www.microsoft.com/downloads/details.aspx?familyid=ad724ae0-e72d-4f54-9ab3-75b8eb148356&displaylang=en")

That list should be sufficient enough for most things.
Though I'll have to admit, that they aren't all Realtime-Scanners.

But for everything else.
There is always [http://www.wiki-security.com](http://www.wiki-security.com) (For Manual Removal of Viruses/Spyware)

[EDIT]
clamav should have real-time snanning for Windows.
I've installed it before. And putting "C:\PATH\TO\CLAMDSCAN --options --options" in my startup list seems to work.
Though back then my hard drive had an error somewhere because I got an error messages like "Cannot read from location 0000xca0000" or somethng of another.

Regards
Iain

---

### Post by seeker1458 on 2008-04-16
> **eXtreem said:**
> It looks like if you install clamwin together with winpooch you have a realtime virusscan...

winpooch you can find here: [http://winpooch.free.fr/page/home.php?lang=en&page=home](http://winpooch.free.fr/page/home.php?lang=en&page=home)

Tried installing Winpooch. 99% of system usage. Could be my system, but I doubt it.  I tried killing it a couple of different times and re-launching it.  Kept hosing the system.

---

### Post by seeker1458 on 2008-04-16
Why is quality free software limited to the *nix world?  Even most of the free ware for OS X is crap.

---

### Post by sports fan Matt on 2008-04-16
What about AVAST? [http://www.avast.com/](http://www.avast.com/)

---

### Post by seeker1458 on 2008-04-16
> **sox fan Matt said:**
> What about AVAST? [http://www.avast.com/](http://www.avast.com/)

See original reason for post.  Trying to find a way LEGALLY to use this in commercial setting. Looking for something protected under GPL that I don't have to worry about getting the company sued.

---

### Post by heartburnkid on 2008-04-16
> **seeker1458 said:**
> Why is quality free software limited to the *nix world?  Even most of the free ware for OS X is crap.

*nix tends to attract a lot of coders that are really into the whole Free Software philosophy.  And, ironically, most Free Software developers are quite selfish; if it works on their platform of choice, they aren't going to worry about porting it to others too much. Still, most of the good stuff eventually gets ported over to other platforms, but the ports often aren't quite as good (not to say that they're bad).

Anyway, there's your solution; switch your sales team to Linux. :)

---

