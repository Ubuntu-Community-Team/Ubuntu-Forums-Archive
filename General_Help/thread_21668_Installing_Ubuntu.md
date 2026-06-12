---
title: "Installing Ubuntu"
date: 2005-03-23
forum: General Help
---

### Post by LOOregano on 2005-03-23
I am not sure if I am posting this in the right area, but I am new to ubuntu and don't yet now how to us it or the web forum

I am trying to install Ubuntu and the directions just say to burn the file and then put the cd in and restart the computer.  I do that and nothing happens.  I curently am trying to demolish windows 98.  How do I install this when restarting with the CD burned image 
Ubuntu 5.04 Preview "The Hoary Hedgehog"

I downloaded it from the mirror found at
[http://ubuntu.mirrors.tds.net/releases/5.04/](http://ubuntu.mirrors.tds.net/releases/5.04/)
and saved to my desktop (and then burned) the link entitled
:Intel x86 installation CD
for my  PC.  I know this is elementry but I hope someone can help me past this first stage.

thank you!

---

### Post by StacyWebb on 2005-03-23
Just curious, did your burn the iso (using Nero or other) or did you just copy the iso to the CD? The reason I ask is becuse iso is just an image file and with windows you would need a third party app to create the install cd from the iso.

---

### Post by LOOregano on 2005-03-23
I think that I used Roxio to burn it but sometimes I use the direct cd function and just drop it in the cd as an image and then burn it.  Should I try doing it directly through Roxio?

---

### Post by Buffalo Soldier on 2005-03-23
What I suggest is:[list=1]
[*] Backup your data (if there's any that you would like to continue using in Ubuntu)
[*] Suggest you use Warty 4.10 rather than Hoary 5.04. Hoary is still in beta (preview). But if you feel adventurous... :) 
[*] Download the iso and perform a checksum.
[*] Set your BIOS so that it boots the CD first.
[*] Insert CD and reboot
[*] Don't panic if there's something you don't understand from a quick read. Take your time to read the instruction. Sometimes easy and trivial things seems hard if it's in an unfamiliar environment.
[/list]

---

### Post by LOOregano on 2005-03-23
I apologize, but I do not know how to perform a checksum or set my system bios.  I looked around on the internet and in help functions, but was entirely unsucessfull.  How may I do these, or if it is complicated can you refer me to a helpfile, or something of the likes?

Also my friend who recomended me to Ubuntu, recommended also that I download the preview Hoary version saying that it was probably better then the previous, even though it was a preview.  I downloaded this version when I was on a direct connection, but now I am home from spring break and am on a dial up...so downloading the other version now may seem a bit impratical.  

Thank you,
Lawrence

---

### Post by Kanna on 2005-03-23
a checksum is to see if your download is not corrupted, and is fairly easy to use. You need to download a little program to do this for you. You could probably easy find one at google, but here is an example: [http://www.fastsum.com/download.php](http://www.fastsum.com/download.php)

To go into your BIOS you hit a key right when the computer boots up. Usually this is 'del'. It should say somewhere on the first screen that appears. in there you can somewhere find what order it tries to boot at, just make sure your cd-rom is first in the list.

Hope that helps =)

---

### Post by LOOregano on 2005-03-23
okay, I got the checksum to work and the output is:

"Calculations summary:
  Processed 1 files in 0 folders with total size of 533.29Mb.
  Elapsed time:   ...etc"

so does this mean it checks out?
Should I try reburning the cd?

thank you,
Lawrence

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=LOOregano]okay, I got the checksum to work and the output is:

"Calculations summary:
  Processed 1 files in 0 folders with total size of 533.29Mb.
  Elapsed time:   ...etc"

so does this mean it checks out?
Should I try reburning the cd?

thank you,
Lawrence[/QUOTE]
 Is that all of the output?

---

### Post by LOOregano on 2005-03-23
That seemed to be the only interesting part.  But I will now type out everything (since I cannot highlight cut or paste).
I typed in from the command prompt:
c:\>  fsum  "C:\Documents and Settings\Bozo\Desktop\downloads\hoary_preview_instal__i386.iso"

and the output was:
"
MD5 Checksum calculation and verification utility. [1.9.0.149] EN
(C) 2003-2005 Kirill Zinov and Vitaly Rogotsevich. Web site: [www.fastsum.com](www.fastsum.com)

C:\Documents ...\hoary_preview_instal__i386.iso 0F04DE0A00E922CDA2E6C49C37ECEB7F


Calculations summary:
Processed 1 files in 0 folders with total size of 533.29Mb.
Elapsed time: 00:00:44 Average speed: 12.20 Mb\Sec.
"
hope the extra info helps solve my problem.

---

### Post by Buffalo Soldier on 2005-03-23
I think fastsum is more geared towards creating md5sum rather then checking it.

But try [http://winmd5sum.solidblue.ca/](http://winmd5sum.solidblue.ca/)

We had a discussion about it at [http://ubuntuforums.org/showthread.php?t=19703](http://ubuntuforums.org/showthread.php?t=19703)

Once you're thru with that.. we'll deal with setting your BIOS to boot to CD.

Hang tough :)

---

### Post by LOOregano on 2005-03-24
okay I downloaded the new software for running a checksum.  I selected the document and hit calculate.  Other then some processing, no dialog status or result box poped up.  I also tried the compare feature, and the same thing happened:  Processes but no results are shown.  So I guess if it did something, it just didn't tell me what it did or the results.  Is there anything else I can do? should have done?  I left the compare box blank simply beccause I do not know what to put on there.  I cannot find directions in the downloaded material or on the refered website, so I know not how to procede.

Thanks for the encouragement!  It is frustraiting have a time limit and not even being able to begin sucessfully!

---

### Post by Buffalo Soldier on 2005-03-24
Erm, you're suppose to hit **compare**.

I've posted a similiar instruction here: [http://ubuntuforums.org/showthread.php?t=19703](http://ubuntuforums.org/showthread.php?t=19703)

---

### Post by LOOregano on 2005-03-24
yes, I tried hitting compair after reading your direcetions (I origninally tried both methods but both yield the same result. ie no result)

The series in the MD5Sum box came up as:
0f04de0a00e922cda2e6c49c37eceb7f

wait!  okay, I just tried hitting compare again, and now it is saying that the checksums are different.  So does this mean that I need to redownload the files?  If so how do I keep the integrity of the file this time?

---

### Post by Buffalo Soldier on 2005-03-24
Yes you have to download again.

How to keep the integrity? ermm not sure about that. I've been downloading using bittorent. and so far it hasn't fail me yet.

---

### Post by LOOregano on 2005-03-30
I hope someone notices this since I have not been on in a few days.  I have redownloaded the iso now twice and neither check out using the recomended WINMD5SUM program.  In fact, I checked out about 7 other files I have downloaded, of various types, and none of them check out.  When I hit compair all of them tell me the same message:

"MD5 Checksums are different."

What can I do.  I tried two different mirrors (the first two in the list).  How do a get a download to check out?

Using bittorent was suggested but I do not know what that is, or how to change it.  If this might work, could someone tell me how to change to bittorent?

Thank you.

---

### Post by LOOregano on 2005-04-08
Is anyone there?  I am still not able to do what I said above.  Is anyone able to help?

---

### Post by Buffalo Soldier on 2005-04-08
[QUOTE=LOOregano]I hope someone notices this since I have not been on in a few days.  I have redownloaded the iso now twice and neither check out using the recomended WINMD5SUM program.  In fact, I checked out about 7 other files I have downloaded, of various types, and none of them check out.  When I hit compair all of them tell me the same message:

"MD5 Checksums are different."

What can I do.  I tried two different mirrors (the first two in the list).  How do a get a download to check out?

Using bittorent was suggested but I do not know what that is, or how to change it.  If this might work, could someone tell me how to change to bittorent?

Thank you.[/QUOTE]Sorry for the late reply. Lets see what we can do here.

OK first let's double check your MD5SUM. The steps that I would take are:[list]
[*] Go to -> [http://releases.ubuntu.com/hoary/](http://releases.ubuntu.com/hoary/)
[*] Download the Hoary i386 installation CD iso file ->[http://releases.ubuntu.com/hoary/ubuntu-5.04-install-i386.iso](http://releases.ubuntu.com/hoary/ubuntu-5.04-install-i386.iso)
[*] And then download the file containing the MD5SUMS list -> [http://releases.ubuntu.com/hoary/MD5SUMS](http://releases.ubuntu.com/hoary/MD5SUMS)
[*] After finish downloading both files. Compare the checksum of the ISO that you've downloaded with the MD5SUMS.
[/list]

Q: What is BitTorrent? 
A: [http://www.bittorrent.com/introduction.html](http://www.bittorrent.com/introduction.html)

Q: Where to download a BitTorrent client?
A: [http://www.bittorrent.com/index.html](http://www.bittorrent.com/index.html)

Q: Is there any other BitTorrent client?
A: Yes, there are many. And the one I like to use when I'm in M$ Windows is [Azureus](http://azureus.sourceforge.net/).

And if you would like to try downloading using torrent method:[list]
[*] Download and install BitTorrent client of your choice.
[*] Go to -> [http://releases.ubuntu.com/hoary/](http://releases.ubuntu.com/hoary/)
[*] [*] Download the Hoary i386 installation CD iso **torrent** file ->[http://releases.ubuntu.com/hoary/ubuntu-5.04-install-i386.iso**.torrent**](http://releases.ubuntu.com/hoary/ubuntu-5.04-install-i386.iso.torrent)
[*] After downloading the torrent file, double click it and it will be automatic open by your BitTorrent client.
[*] If that does not happen. Run your BitTorrent client first then the open the torrent file from there. (i think it's something like File -> Open > browse torrent file)
[*] Then your BitTorrent client will ask you where would you like to save the ISO file. 
[*] Your BitTorrent client will then go hunting for the ISO all around the world and download them to your computer and it should automatic check your MD5SUMS.
[/list]

I hope I manage to cover all the steps. If I missed any... please someone fill in the gaps.

Glad that you're still trying to download Ubuntu eventhough it seems like a hassle. Keep up your spirit.

---

