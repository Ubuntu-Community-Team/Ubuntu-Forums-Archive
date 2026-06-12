---
title: "Are there any anti-spyware programs for Ubuntu?"
date: 2008-04-21
forum: General Help
---

### Post by Antarctica on 2008-04-21
Hey, I'm trying to fix my boss's computer, and I was wondering if there are any anti-spyware programs for Ubuntu that I could download and install.  I want to put his hard drive into my computer and run an anti-spyware and anti-virus scan using Ubuntu if possible.  If not, I'll just have to boot from Windows on his hard drive then.

---

### Post by xaenyx on 2008-04-21
Anti spyware/virus to scan the *windows* partition?

---

### Post by overdrank on 2008-04-21
> **Antarctica said:**
> Hey, I'm trying to fix my boss's computer, and I was wondering if there are any anti-spyware programs for Ubuntu that I could download and install.  I want to put his hard drive into my computer and run an anti-spyware and anti-virus scan using Ubuntu if possible.  If not, I'll just have to boot from Windows on his hard drive then.

HI and this link may help
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by vishzilla on 2008-04-21
First Linux doesn't need an anti-virus nor an anti-spyware coz viruses don't affect Linux systems. If you have Windows systems in your network, probably you need an anti-virus like clamAV.

---

### Post by Antarctica on 2008-04-22
Yeah.  See, I'm putting my boss's hard drive into my computer as a slave drive.  His hard drive has Windows XP installed onto it.  What I want to do is use my computer (running Ubuntu Hardy) to scan his hard drive for spyware and viruses, and I was wondering if there are any programs that can do that.

---

### Post by Lantesh on 2008-04-22
Avast makes an anti-virus program for Linux.  You can download it for free here:  [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)  .  Just download the deb package.  Double click to install.  You will have to register it, and they will give you a serial number for it, but it's free.  The registration doesn't really ask for much.  I didn't even give my full name or anything.

---

### Post by Antarctica on 2008-04-22
I think I'm just going to boot from his hard drive and try to repair the problems from there.

---

### Post by eriqjaffe on 2008-04-22
> **Antarctica said:**
> I think I'm just going to boot from his hard drive and try to repair the problems from there.It's not a Linux-based solution, but you might want to look into building a BartPE disk for such situations.  It's about as close as you're going to get to a Windows XP Live CD.  I use one at work all the time, and it's a lifesaver when I have to deal with heavily infested systems.

---

### Post by p.becks on 2008-04-22
Tell your boss not to watch so much porn.. :-)

---

### Post by jespdj on 2008-04-22
> **Antarctica said:**
> I think I'm just going to boot from his hard drive and try to repair the problems from there.
You mean, you have your boss' harddisk with Windows XP in your computer now and you're going to boot from it in your computer?

That will most likely not work well, unless your computer has the exact same hardware as your boss' computer, and even then you will most likely get problems with Windows XP - it will probably start complaining that Windows has to be activated again.

Windows is not as easy as Ubuntu in this regard.

---

### Post by 3rdalbum on 2008-04-22
Remember, if you find viruses or spyware, you really will need to format the drive and reinstall Windows to be able to guarantee the integrity of the operating system.

---

### Post by duckville on 2008-04-22
To be really safe...
you can use a lifeCD (live CD) of ubuntu, sudo apt-get update && sudo apt-get install clamav.

Everything is being stored in RAM, then scan your boss's mounted WinXP HD.
clamav with help with viruses, not anti-spyware.

---

### Post by ibuclaw on 2008-04-22
Spyware is a problem that only affects Windows, not Linux...

---

### Post by FredB on 2008-04-22
If you stay with official repositories and well known ones, you won't get any troubles.

---

### Post by Linux&amp;Gsus on 2008-04-22
> **p.becks said:**
> Tell your boss not to watch so much porn.. :-)
Or use Linux for that purpose :popcorn:

*SCNR* :oops:

---

### Post by ibuclaw on 2008-04-22
> **Linux&Gsus said:**
> Or use Linux for that purpose :popcorn:

*SCNR* :oops:

What ever happened to your wives?
Don't they have a say?
:popcorn:

Just block keywords/sites with your router, that's what I've done :)

Log into Router (type 192.168.1.1 into Firefox)
*username*
*password*
Enter the page->Block Sites:
And type in some sensitive keywords.
Apply!

I have a Netgear WPN824v2 Router btw, so it may not work for you.

[EDIT]
Refer to your Router Manual, or your Router Box
ie:
On the bottom of mine it read:
Access: [http://192.168.1.1](http://192.168.1.1)
Username: admin
Password: password

This can be changed once you login...

Regards
Iain

---

### Post by jen1963 on 2008-04-23
AVG make a free anti virus for Linux which may be able to disinfect an NTFS partition if you have NFTS read\write enabled. The Free AVG Anti Virus for Linux is at:
[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

There is no spyware scanner for Linux I know of as they are is yet spware for Linux I've heard of either. Sorry to say that Malware remains a WinBLOWS problem...

---

### Post by jlh68 on 2008-04-23
I agree with the above, I can't even get my WindozeXP Hard Drive to boot up after changing my mother board.  It just wants to be "Activated" and I click yes and then it says it is Activated and shuts down.  That is the cycle, and I can't seem to figure out how to get it to boot.

But thanks to Ubuntu Linux, and an USB to IDE adapter, I have been able to access my files and move them to another computer.

It is more and more looking like that Windoze HD may become a second Ubuntu HD.

---

### Post by C. Wizard on 2008-04-23
What the op has proposed will work. I've done it.  Set up your boss' hd as a slave and use AVAST to scan it and remove viruses.

---

### Post by oldsoundguy on 2008-04-23
Get thee to a clean Windows machine and download ClamWin, Spybot Search & Destroy, SuperAntiSpyware, A Squared Free, Glary Utilities and CCleaner and burn them to a BOOTABLE cd (use a RW so you can update occasionally).  Then boot with it on your bosses computer and start vacuuming the garbage out.  (none of those programs will cost you a dime!)

Then install FREE AVG (dump Norton or whatever he has), add Spyware Blaster and Spyware Guard, SuperAntiSpyware, Spybot Search & Destroy with the immunization activated (not tea timer) and a real goodie (paid) Prevx 2.0.

The MAIN reason I have stopped using Windows based computers ON LINE .. they are fine for multi media and games, photography and music (although Apple is better in those areas) .. useless for anything else anymore as you have to spend HOURS installing and maintaining protection programs and additional hours RUNNING cleanup programs

---

### Post by Lantesh on 2008-04-26
> **oldsoundguy said:**
> The MAIN reason I have stopped using Windows based computers ON LINE .. they are fine for multi media and games, photography and music (although Apple is better in those areas) .. useless for anything else anymore as you have to spend HOURS installing and maintaining protection programs and additional hours RUNNING cleanup programs

That is an excellent point, and one of the reasons I too am a Linux user.  It is just too easy for a Windows box to get infected anymore, and I just don't want to be bothered with that nonsense anymore.  I boot into Windows to play games.  Everything else these days I do in Linux.

---

### Post by ktechman on 2008-05-02
After making the switch to 7.1 my biggest concern isn't what new threat I am going to have to guard against in Windoz but which Ubuntu distro I am going to use Gutsy, Hardy- Gutsy, Hardy???? Hmmm think I'll use both...........LOL all the way to the bank.

---

