---
title: "Emergency!!!  How the deuce do i UNDELETE stuff?  It bypassed the trash"
date: 2007-10-30
forum: General Help
---

### Post by bluepowder7 on 2007-10-30
oh damn!!!  long story short, i mistakenly deleted a folder in the / partition that i THOUGHT was an EMPTY duplicate of my /home partition, but for some strange reason it started blowing away my actual home folder in the /home partition.  it said that it's deleting and not going via the trash can.  by the time i realized that it's blowing away files that would never have been in the duplicate, a few seconds elapsed.  now, a bunch of files from my /home partition are gone.

um, how do i get the back?????  they ain't in the trash can!  i'm a newb, and by the looks of it a very hosed newb...

---

### Post by Ranhiru on 2007-10-30
> **bluepowder7 said:**
> oh damn!!!  long story short, i mistakenly deleted a folder in the / partition that i THOUGHT was an EMPTY duplicate of my /home partition, but for some strange reason it started blowing away my actual home folder in the /home partition.  it said that it's deleting and not going via the trash can.  by the time i realized that it's blowing away files that would never have been in the duplicate, a few seconds elapsed.  now, a bunch of files from my /home partition are gone.

um, how do i get the back?????  they ain't in the trash can!  i'm a newb, and by the looks of it a very hosed newb...

Well maybe you can try re-installing Ubuntu! (Assuming you lost some files belonging to the functionality of the OS!)
Or else im not really sure but there maybe third party file recovery applications! I have loadz for Windows. But as still im a newbie too i dont know about such applications for Ubuntu! The best thing you can do now is not use the hard drive (If its the E: drive...dont copy anything, delete anything or move anything! Coz this will effectively lessen up the chances of your files being recovered by a undelete software)
But wait till an experienced user tells you what to do!

---

### Post by bluepowder7 on 2007-10-30
actually, the files it blew away weren't related to the OS.  it started deleting everything within my /home partition, and by the looks of it it goes backwards through the alphabet, so my "work" folder was first to get hit and from it i lost a bunch of files.  it's not like it was one specific file that i can try to undelete, but rather everything within the /home/work subdirectory as well as whatever files it blew away from /home directly (stuff that isn't in folders, of which thankfully there was very little).

the only good thing is that some files i can recreate since i have them "saved" in e-mails, but those are only the ones that i know about.  that might only be 3 to 5 files.   :(

---

### Post by Ranhiru on 2007-10-30
> **bluepowder7 said:**
> actually, the files it blew away weren't related to the OS.  it started deleting everything within my /home partition, and by the looks of it it goes backwards through the alphabet, so my "work" folder was first to get hit and from it i lost a bunch of files.  it's not like it was one specific file that i can try to undelete, but rather everything within the /home/work subdirectory as well as whatever files it blew away from /home directly (stuff that isn't in folders, of which thankfully there was very little).

the only good thing is that some files i can recreate since i have them "saved" in e-mails, but those are only the ones that i know about.  that might only be 3 to 5 files.   :(

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

try this software buddy! It has a version for Ubuntu as well!

---

### Post by Ranhiru on 2007-10-30
And this is another thread i saw!
[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

same software! he has used in Ubuntu!

---

### Post by larryfroot on 2007-10-30
there are some specialist distro's - usually based on knoppix which is the god of live cd's - that errr...specialise in security/forensics/data recovery. Just load up the distro into the ram and sort out the data recovery on your hard drive from there. You can at least take a look and see if there are any tools in any of them that can help you. I think so, though. There is a really decent rundown of a selection of them with handy links [here]("http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/")

Hopefully you will find one suitable for your needs, there are a couple who have data recovery software on them, which might mean another learning curve, but hey...if your any of your mates data gets swallowed up and you rescue it = kudos + free beer. Good luck, though.

Oh, just one thing...as the distro you will be using is live ie sat in the ram you would think it the most reasonable thing in the world to just switch off your PC when done without bothering to exit the live cd from the menu as if it was a 'real' installation on your hard drive. However there are some instances where the live distro will only save / execute / on a proper shutdown through its menu - just as if it was on your hard drive. So be sure to exit the live cd nicely...

---

### Post by lsmobrian on 2007-10-30
I would recommend [backtrack]("http://www.remote-exploit.org/backtrack.html")
(It was already said, but dont use that hard drive if possible, download and burn on another computer)

it sounds like you need to use the tool foremost.  It doesnt have a GUI that i know of, but its not too complicated.  You will need something to copy the files too like a large USB thumb drive or external hard drive.  I think backtrack will automount, but not sure

you will need to figure out all the file types you are looking for (ie jpg, doc, txt, etc..)

to recover all jpg and txt your command will look something like this

foremost -t jpg,txt -o /mnt/sdb_removable -i /dev/hda

run "man foremost"  if you need more explanation 



I dont know if this is the best way or if there are better tools, but its all I've ever used

---

### Post by bluepowder7 on 2007-10-30
ok, i made a copy of what was left of my /home partition onto a removable drive and then from that onto a whole other pc's hard drive, and now i'm running foremost on the hosed folder.  any ideas on how long the process actually takes?  i punched in the command:

foremost -d -T -t all -i /home/greg/work -o /media/disk/recover

to which it replied:

Processing:  stdin
| XX

where XX is the non-blinking block cursor.  and yeah, there's a | character just before it.  i suppose i can let it run for a half hour or so, but is there something that it SHOULD be displaying eventually as a sign of progress???

---

### Post by lsmobrian on 2007-10-30
foremost works by looking through the entire device looking for file signatures.  so it will look through /dev/hda ... it cant look just in one folder.  Using this tool its gonna take finding all file types on the entire drive and then sorting through them once its done and finding which ones were the ones that got deleted. like i said i dont know if this is the best way, but its the only way I have used


ex:  foremost -t jpg,txt -o /mnt/sdb_removable -i /dev/hda


will look through your hard drive (/dev/hda) for all jpg and txt file signatures(everywhere on the drive deleted or not) and copy the files to your USB thumb drive /mnt/sdb_removable or whatever name is used when mounting


when its running it will say processing /dev/hda
and it will take a while depending on the size of your hard drive
if you have lots of files to be recovered and a small USB drive, you may have to run it one at a time for each file type

---

### Post by bluepowder7 on 2007-11-01
update:

well, i tried foremost a few different ways, and i wasn't able to recover anything.  lesson learned!  i guess the first thing to do on the next reinstall of everything is using an exf2 partition instead of exf3.  that, and doing backups!!!

---

