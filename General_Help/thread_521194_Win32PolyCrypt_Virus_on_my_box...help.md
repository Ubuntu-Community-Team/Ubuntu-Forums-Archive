---
title: "Win32/PolyCrypt Virus on my box...help?"
date: 2007-08-09
forum: General Help
---

### Post by DarkStarAeon on 2007-08-09
Ok, been running Ubuntu (and other distros) for about two years now quite happily, and even though it's not really thought of as necessary I still scan for viruses every single day...give me a break, Windows conditioned me to do it for years ;)

So anyway, I've never had a virus of any kind for any system on a Linux box before, so my question is:

How do I remove a Windows virus from a Linux machine? 

I did a scan with AVG (for some reason Clam has never been able to run on my computer) and to my surprise it showed me that I have Win32/PolyCrypt in multiple locations on my computer.

I know I can't just delete the files as many are needed files. Some listed I don't know what they are, but many I recognize.

Anyone know what I should do? I don't want to pass this on to Windows users.

**Here's the infected files output...**

```

etc/alternatives/x-session-manager
usr/bin/as
usr/bin/evolution
usr/bin/evolution-2.10
usr/bin/evolution-2.2
usr/bin/gdbserver
usr/bin/gencat
usr/bin/gnome-session
usr/bin/gnome-system-monitor
usr/bin/mawk
usr/bin/msgunfmt
usr/bin/vmnet-dhcpd
usr/bin/x-session-manager
usr/lib/libgettextsrc-0.16.1.so
usr/lib/libgettextsrc.so
usr/lib/libneon.so.25
usr/lib/libneon.so.25.0.5
usr/lib/libportaudio.so.0
usr/lib/libportaudio.so.0.0.18
usr/lib/libuniquewm-0.9.so.25
usr/lib/libuniquewm-0.9.so.25.0.0
usr/lib/gnome-applets/cpufreq-applet
usr/lib/gnome-pilot/conduits/libmal_conduit.so
usr/lib/gnome-vfs-2.0/modules/libhttp.so
usr/lib/gstreamer-0.10/libpitfdll.so
usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so
usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjdwp.s0
usr/lib/openoffice/program/configimport.bin
usr/lib/openoffice/program/dlgprov680li.uno.so
usr/lib/openoffice/program/libdbpool2.so
usr/lib/openoffice/program/libgcc3_uno.so
usr/lib/openoffice/program/libjava_uno
usr/lib/openoffice/program/libjava_uno.so
usr/lib/openoffice/program/liburp_uno.so
usr/lib/openoffice/program/libxsltfilter680li.so
usr/lib/openoffice/program/proxyfac.uno.so
usr/lib/openoffice/program/servicemgr.uno.so
usr/lib/openoffice/program/uno.bin
usr/lib/openoffice/program/vbaevents680li.uno.so
usr/lib/sane/libsane-pixma.so.1
usr/lib/sane/libsane-pixma.so.1.0.18
usr/lib/vmware-player/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-ico.so
usr/lib/xorg/modules/libddc.so
usr/sbin/pam_tally

```

For a virus that's supposed to be just for Windows, it sure does know how to spread itself around a Linux operating system.

I can't find any info on how to remove Windows viruses from a Linux machine, maybe I'm searching for the wrong thing?

---

### Post by hikaricore on 2007-08-09
You really can't get a ***dows virus on a Linux system.

I'm going to guess false positives?

---

### Post by DarkStarAeon on 2007-08-09
Is there a good way to double check? I didn't have this yesterday, or anything else before it, now today it shows up all over my filesystem, that's a lot of false positives.

I just don't want to pass it on. My system is running happily as always, but my wife has Ubuntu and Windows on her computer, I'd hate to accidentally send her something that messes up her machine.

---

### Post by splintercellguy on 2007-08-09
IMHO totally a false-positive. Not sure how a Windows virus could even infect an ELF library.

---

### Post by DarkStarAeon on 2007-08-09
Alright, I'll take both your words for it, thanks for replying :)

---

### Post by Ahunt on 2007-08-09
This is an interesting issue. I have just done an AVG update on my Ubuntu box (7.4) and came up with 44 infections in similar locations as mentioned here.

I scanned the AVG Linux user forum [http://forum.grisoft.cz/freeforum/list.php?10](http://forum.grisoft.cz/freeforum/list.php?10) and didn't find any mention of this problem, except for one Windows XP infection of it.

I have sent a question to the AVG team via the forum [http://forum.grisoft.cz/freeforum/read.php?10,106006,backpage=,sv=](http://forum.grisoft.cz/freeforum/read.php?10,106006,backpage=,sv=) In the past I have found them pretty quick to respond and very helpful. I will post a note back here when I hear from them.

Adam

---

### Post by LRT on 2007-08-09
I just found this very same virus (Win32/PolyCrypt) on my Windows Small Business Server 2003. I am also using AVG 7.5 Network Edition. Any idea on how to get rid of this? Is it a dangerous virus?? I am in a business environment, any help would be greatly appreciated. Thanks!

LRT

---

### Post by Super TWiT on 2007-08-09
I believe that AVG scans for windows viruses only.  These viruses have no effect on Linux and the only reason you would want to run an anti virus would be to make sure you didn't spread a virus to a windows machine.  Whenever, a security hole is found it is patched quickly, so  the only thing you have to really do on Linux is make sure you download all the updates.

---

### Post by isaacj87 on 2007-08-09
If you want, you guys finding the PolyCrypt can download Avast! and see if it produces the same results.

---

### Post by Super TWiT on 2007-08-09
> **Super TWiT said:**
> I believe that AVG scans for windows viruses only.  These viruses have no effect on Linux and the only reason you would want to run an anti virus would be to make sure you didn't spread a virus to a windows machine.  Whenever, a security hole is found it is patched quickly, so  the only thing you have to really do on Linux is make sure you download all the updates.

My above post was meant for Ahunt.  I guess I type too slow!:)

---

### Post by Tauceti38 on 2007-08-09
I also just received these warnings about win32/polycrypt today when my ubuntu partiton was scanned. I'm currently running avg in windows, and have windows configured to be able to read my linux partition.

I suspect that these are false positives caused by the last update released for avg. The last update I received was earlier today, presumably before the current scan began. A quick google search for "Win32/PolyCrypt" returned this thread, and several others posted today on other sites. That alone make me suspect the problem is with avg.

---

### Post by Ahunt on 2007-08-09
Thanks for your thoughts on that. I had gathered from doing some internet searches that this virus was specific to Windows systems only and cannot affect Linux systems. that doesn't explain how it is detected as being all over the Ubuntu system. If the virus doesn't work on Ubuntu then it shouldn't have spread in the system. It especially shouldn't be found in files that require a password to modify!

I have just checked my AVG forum post to see if there is an answer there and it looks like the forum staff have moved the question and provided an answer, although not a conclusive one. 

The thread can now be found at [http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=,sv=](http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=,sv=) 

As I have indicated I will run a test on one of the files and report on both forums what I find.

Adam

---

### Post by 94q45t on 2007-08-09
> **Super TWiT said:**
> I believe that AVG scans for windows viruses only.  These viruses have no effect on Linux and the only reason you would want to run an anti virus would be to make sure you didn't spread a virus to a windows machine.  Whenever, a security hole is found it is patched quickly, so  the only thing you have to really do on Linux is make sure you download all the updates.

I'm a windows interloper, but just googled Polycrypt and found this thread. I know my PC has always reported virus free with the most recent scan being yesterday by Kasperski v7.0.125. However, that build caused some problems, so I rolled back to AVG Pro v7.5.  The first scan it did found polycrypt on some excel files that are 8 years old.  These files have been inactive (not reviewed or opened in Excel) since then, and are archive files.  Because this PC has been scanned by a variety of AV programs daily for years, my belief is that this is a false positive.  The Google results suggest others think so to.  The detection seems to be unique to AVG.

Hope this helps.

---

### Post by splintercellguy on 2007-08-09
> **Ahunt said:**
> Thanks for your thoughts on that. I had gathered from doing some internet searches that this virus was specific to Windows systems only and cannot affect Linux systems. that doesn't explain how it is detected as being all over the Ubuntu system. If the virus doesn't work on Ubuntu then it shouldn't have spread in the system. It especially shouldn't be found in files that require a password to modify!

I have just checked my AVG forum post to see if there is an answer there and it looks like the forum staff have moved the question and provided an answer, although not a conclusive one. 

The thread can now be found at [http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=,sv=](http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=,sv=) 

As I have indicated I will run a test on one of the files and report on both forums what I find.

Adam

The virus definition caused a false positive, nothing to see :P.

---

### Post by prstl on 2007-08-09
I am a W*nDoWs   Senior Systems Administrator who now uses Ubuntu on all my personal PC's.   Having done an AVG virus scan today on one of my personal boxes I was surprised when I found 3 of my files potentially infected.

I uploaded one of these files to virusscan.jotti.org to do a quick scan using their system.  Below is the results.... Interesting for now.... 
a false positive... maybe....maybe not...  I am going to keep a close watch on this.  



 File:  	 awk
Status: 	
INFECTED/MALWARE
MD5: 	f4175e2f0960e810bd8dd340b70637b5
Packers detected: 	
-
Bit9 reports: 	File not found
Scanner results
Scan taken on 09 Aug 2007 17:07:12 (GMT)
A-Squared 	    Found nothing
AntiVir 	        Found nothing
ArcaVir 	       Found nothing
Avast 	                Found nothing

[COLOR="Red"]AVG Antivirus       Found Win32/PolyCrypt[/COLOR]

BitDefender 	            Found nothing
ClamAV 	                    Found nothing
CPsecure                   Found nothing
Dr.Web 	                    Found nothing
F-Prot Antivirus           Found nothing
F-Secure Anti-Virus     Found nothing
Fortinet 	               Found nothing
Kaspersky Anti-Virus   Found nothing
NOD32 	                    Found nothing
Norman Virus Control  Found nothing
Panda Antivirus 	  Found nothing
Rising Antivirus 	   Found nothing
Sophos Antivirus 	 Found nothing
VirusBuster 	           Found nothing
VBA32 	                    Found nothing

---

### Post by DarkStarAeon on 2007-08-09
Yeah, think you're still right splintercellguy ;)

I just downloaded and tried avast, here is the result:

# Statistics:
#
# scanned files:        116767
# scanned directories:  6137
# infected files:       0
# total file size:      26.3 GB
# virus database:       000714-0 15.02.2007
# test elapsed:         10m:34s 4ms
#

I also tried Aegis, same deal.

I appreciate Ahunt taking the time to dig deeper though just in case, and if AVG gets back to you I'd like to know what they have to say.
I do think it had to do with the last update from AVG, I had nothing before that and suddenly I got that result which I started this topic with. Must be AVG.

---

### Post by Ahunt on 2007-08-09
Hi again everyone:

Well I *think* we have an answer on this one, with input from Grisoft. As the consensus on this forum agreed from the start it is *likely* a false-positive. It also seems that it is uniquely a Linux problem as I don't see users reporting this happening on other OS. At least not on the AVG forum.

Perhaps I have been living in a cave all these years but I did learn something new from this issue: The existence of [http://virusscan.jotti.org/](http://virusscan.jotti.org/) which gives the capability to test any file against 20 different virus scanners. A nice little tool to know about!

The complete thread of this discussion with Grisoft is there on the AVG forum at [http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=2,sv=](http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=2,sv=)

As usual the AVG folks seem to have all the answers, happily presented with a snarl. Must be a "cross cultural" thing.

I would like to thank everyone on this forum; as usual the Ubuntu community is a great resource and polite to each other, too.

I will perhaps post again here when the AVG definition files are updated and the scans are clear, just so future readers of this will know how it all ended.

Adam

---

### Post by DarkStarAeon on 2007-08-09
Awesome, thanks man, I appreciate you digging deeper, and I dig the Ubuntu community too. :)

Let us know if you find anything else, or don't find anything else, lol

---

### Post by Ahunt on 2007-08-09
A further update on this issue:

As described above, when I did my AVG scan this morning I had "44 viruses" on my Ubuntu PC. After the discussions with Grisoft on their forum as described above, I downloaded a new virus definition file 269.11.11/944 and rescanned the PC. This time AVG came up with just one "infected file" /usr/bin/mawk. I hadn't taken any other action other than downloading the new definition file.

I tried turning the AVG heuristic scanner off and it still detects it. I ran it through [http://virusscan.jotti.org/](http://virusscan.jotti.org/) and only AVG flagged it. The other 19 scan engines there called it "clean".

I think the fact that the previous 43 virus "finds" all disappeared with the latest update indicates that, indeed, this was a "false alarm" issue.  I think the folks at Grisoft had a busy day today there fixing this one.

Coincidently I ran a manual AVG system scan with the latest definition file on my Windows XP box while all this Ubuntu virus scare was going on and AVG detected a "Trojan". The file it claimed was infected is my archived installation file for Ad-Aware 2007, a free anti-spyware program. AVG happily deleted it for me.

I will try to add at least one more update when the Ubuntu box is totally clear.

Adam

---

### Post by EXCiD3 on 2007-08-09
One of the problems is probably that other than AVG and Clam, there isnt much out there scanning for linux viruses. This really sucks that once Ubuntu takes off there will be loads of viruses being made for Ubuntu now (you may have to do ./configure, make, and make install first ;)).

---

### Post by DarkStarAeon on 2007-08-09
Geesh, what a mess at AVG. Thanks Adam for the update.

I just removed AVG entirely, they are normally good, but they let me down a few times critically when I used Windows and I just don't care to repeat it with Linux.

I installed Avast and Aegis, they seem to to a good job.

I wouldn't worry about AV software for Linux in the future though, as the amount of viruses grows, so too will the companies desire to sell AV solutions to Linux users. They just don't try hard now because most people don't really see a need for their products. But things will change as Linux grows and the threats for it do. Honestly, I'm glad that I don't really "need" an AV solution that badly for Linux. lol

---

### Post by EXCiD3 on 2007-08-09
This joke is doing the rounds. I thought you would all appreciate it, if you
haven't seen it already that is...
 
 -------------------------------------------------------------------------------------------------------------------------
 The Unix (Linux) version of the ILOVEYOU virus works on the honour system.
 
 If you receive this message, you should delete a bunch of GIFs, MP3s and binaries
 from your home directory, and send a copy of this message to everyone you know.
 ----------------------------------------------------------------------------------

---

### Post by DarkStarAeon on 2007-08-09
hee hee hee, now that is funny! :lolflag:

---

### Post by m3rlinez on 2007-08-10
Hi,

I am running Windows XP and AVG reported that there are 20 infected files in my "Cygwin" folder with "Win32/PolyCrypt" name. This maybe an issue with Cygwin users too. :(

---

### Post by hikaricore on 2007-08-10
> **EXCiD3 said:**
> This joke is doing the rounds. I thought you would all appreciate it, if you
haven't seen it already that is...
 
 -------------------------------------------------------------------------------------------------------------------------
 The Unix (Linux) version of the ILOVEYOU virus works on the honour system.
 
 If you receive this message, you should delete a bunch of GIFs, MP3s and binaries
 from your home directory, and send a copy of this message to everyone you know.
 ----------------------------------------------------------------------------------

ROFLMFAO :lolflag:

I'll get right on that.

---

### Post by hikaricore on 2007-08-10
> **m3rlinez said:**
> Hi,

I am running Windows XP and AVG reported that there are 20 infected files in my "Cygwin" folder with "Win32/PolyCrypt" name. This maybe an issue with Cygwin users too. :(

If you read back a page this was almost 100% confirmed as a false positive.

I suggest finding another trusted free virus scanner (like one of the ones listed a page back) and rescan.

---

### Post by Ahunt on 2007-08-10
Dear m3rlinez

I would suggest uploading one of the suspect files at [http://virusscan.jotti.org/](http://virusscan.jotti.org/) and see what the other scan engines have to say. That is the first step in getting some information as to whether you have a problem, or AVG has a problem!

Adam

---

### Post by misfitpierce on 2007-08-10
You can get the exe onto your machine... Im guessing that if opened in Wine or something it could do a bit of damage to Wine directory maybe if unlucky... I'm going to guess since multiple have it that it could be false pos. as stated. I would either say go crazy to all locations and shift+delete manually if your crazy about it or just let it be as its prob a false pos. and I highly doubt you will spread it unless you send the file specifically. :)

---

### Post by Ahunt on 2007-08-10
Just an update on this issue:

The latest AVG virus definitions files came out this morning (269.11.13/946). Scanning with it still showed up /usr/bin/mawk on my Ubuntu PC as being infected with Win32/PolyCrypt. A run through of the file at [http://virusscan.jotti.org/](http://virusscan.jotti.org/) still shows AVG as the only scanner that thinks this file has a problem, so no change there.

What has changed is on my Windows XP PC. I previously reported that the AVG had labeled aaw2007.exe (the installer for Lavasoft Ad-Aware) as being infected with a Trojan and had deleted it. With the latest definition download (same as the Ubuntu ones)  I tried scanning my back-up copy of the file and it says it is clear. I reinstalled the file to the archive, rescanned it and it still reports clear. So progress is being made.

I will do another post if and when the Ubuntu Win32/PolyCrypt issue clears.

I have a feeling that they are having a busy week over at Grisoft - no coffee breaks this week!

Adam

---

### Post by etacarinae on 2007-08-10
> **Ahunt said:**
> Just an update on this issue:

The latest AVG virus definitions files came out this morning (269.11.13/946). Scanning with it still showed up /usr/bin/mawk on my Ubuntu PC as being infected with Win32/PolyCrypt. A run through of the file at [http://virusscan.jotti.org/](http://virusscan.jotti.org/) still shows AVG as the only scanner that thinks this file has a problem, so no change there.

What has changed is on my Windows XP PC. I previously reported that the AVG had labeled aaw2007.exe (the installer for Lavasoft Ad-Aware) as being infected with a Trojan and had deleted it. With the latest definition download (same as the Ubuntu ones)  I tried scanning my back-up copy of the file and it says it is clear. I reinstalled the file to the archive, rescanned it and it still reports clear. So progress is being made.

I will do another post if and when the Ubuntu Win32/PolyCrypt issue clears.

I have a feeling that they are having a busy week over at Grisoft - no coffee breaks this week!

Adam

The same file with the same problem over here.

---

### Post by JunySan on 2007-08-11
same file found here .....

---

### Post by Ahunt on 2007-08-12
I just did another virus scan with AVG and then ran it through Jotti with the same results - AVG still thinks /user/bin/mawk is infected while all other scan engines don't. It seems that lots of Ubuntu users are having this problem.

The AVG staff at Grisoft have said at [http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=2,sv=](http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=2,sv=) that when this happens the procedure they want is:

"If you suspect a file to be a false positive. Test the file at [http://virusscan.jotti.org](http://virusscan.jotti.org) and if it is a false positive, archive (zip, arc, tar etc) the file using a password and email a copy to [email]virus@grisoft.com[/email] with a brief description as well as the password you used to archive it with."

Since this is a binary file I don't have the skills or the application to create a password protected and zipped version of that to send to them. Is there someone else who knows how to do this? Anyone can send them this file from their Ubuntu PC, as it isn't infected. That should speed up getting this last issue cleared!

Adam

---

### Post by folgers on 2007-08-13
I have five files in three computers that AVG reports as infected.

"/etc/alternatives/awk"  Virus found Win32/PolyCrypt
"/etc/alternatives/nawk"  Virus found Win32/PolyCrypt
"/usr/bin/awk"  Virus found Win32/PolyCrypt
"/usr/bin/mawk"  Virus found Win32/PolyCrypt
"/usr/bin/nawk"  Virus found Win32/PolyCrypt

Program version 7.5.47
Virus database version 269.11.17/951

Only AVG at [http://virusscan.jotti.org](http://virusscan.jotti.org) reports them as being infected.

---

### Post by Ahunt on 2007-08-22
Hi again everyone,

Well I promised to post another entry here when this problem was totally cleared and today is that day.

I just downloaded AVG virus definition 269.12.2/966 and ran a scan and it came up clean.

I would suggest anyone who is still having problems with AVG scans detecting a WIN32/PolyCrypt infection should make sure that they have this latest update and then do a scan. It should come up clear.

I would personally like to thank everyone who has worked on this issue here on the Ubuntu Forum for all their help. I really think that beginners and experts alike all helped each other to a great degree. It is this level of support that makes Ubuntu worth using. I would also like to remark on the degree of politeness - it was exemplary. It is amazing how far a like bit of civility can go. This forum is always great that way (well almost always!)

Adam

---

### Post by Ahunt on 2007-08-23
For a final follow-up on this issue:

I have posted a close to the thread I started on the AVG forum to let Grisoft know that the problem of false WIN 32/PolyCrypt detections seems to have been solved on Ubuntu systems with the release of virus database 269.12.2/966. See [http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=1,sv=](http://forum.grisoft.cz/freeforum/read.php?4,106006,backpage=1,sv=) for that entry.

Also in general it is interesting to read through the AVG forum on virus alerts on any given day and see what is happening. At present there seems to be a record number of what looks like "false alarms" that AVG is dealing with. Anyone can have a look at how busy things are by perusing [http://forum.grisoft.cz/freeforum/list.php?4,page=1](http://forum.grisoft.cz/freeforum/list.php?4,page=1)

In future when Ubuntu users find what they think may be a virus "false alarm" it would probably speed things up to follow AVG's procedures:

1. Test the file at [http://virusscan.jotti.org/](http://virusscan.jotti.org/)
2. If it is a false positive, archive (zip, arc, tar etc) the file using a password and email a copy to [email]virus@grisoft.com[/email] with a brief description as well as the password you used to archive it with.

Reporting it here on this forum would probably help, just to alert other Ubuntu users who have also found the infection alert and are worried about it.

Adam

---

### Post by etacarinae on 2007-08-23
[FONT="Book Antiqua"]*[SIZE="3"]Thanks, problem solved.[/SIZE]*[/FONT]

---

