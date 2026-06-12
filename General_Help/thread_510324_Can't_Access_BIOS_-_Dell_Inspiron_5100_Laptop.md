---
title: "Can't Access BIOS - Dell Inspiron 5100 Laptop"
date: 2007-07-26
forum: General Help
---

### Post by jsosnay on 2007-07-26
I have a 4 year old Dell Inspiron 5100 laptop (512 MB; P4 2.4 GHz; 40 GB HDD).  I am currently dual booting XP(SP2) and Ubuntu 7.04 -- everything in this regard works fine.  However, as of 2 days ago, I decided I needed to resize the XP partition and to use gparted live cd to do so.  

I couldn't boot from the CD so I assumed the disk was a coaster and burned another.  Again, no luck.  I then checked to make sure that my boot priority was set to boot from CD before HDD.  I couldn't.  The splash screen prompts me to hit F2 to access the BIOS.  It won't work.  I've also tried del, F12, esc, alt+esc and many other variations.  I get the Dell splash screen for a couple seconds and then the grub menu comes up.  Again, like I said above both XP and Ubuntu load just fine so the system appears to be working fine except for the inability to access the BIOS.  The cd drive works as well as I am able to read and write discs when I am in either OS.  

I'm wondering if anyone else has experienced this problem and knows how to fix it.  Any help would be greatly appreciated.

---

### Post by tszanon on 2007-07-26
I once had an old computer that had this problem: I tried to enter BIOS, but pressing the key just didn't work.
It was the case of "keep trying": do it until it works. I still don't know why it happened.

---

### Post by jsosnay on 2007-07-26
Thanks -- I spent a good 20 minutes last night resetting and pressing buttons.  Maybe it'll work one of these times.

---

### Post by manndani on 2007-07-26
Don't know if there'll be any help here, but here's a link to Dell Bios updates, you can have a look.
[http://tinyurl.com/2hennn](http://tinyurl.com/2hennn)

---

### Post by jsosnay on 2007-07-27
I&#8217;ve since found several links to forum threads that may or may not yield any results.  I have not yet had the opportunity to try any of the fixes suggested, however, I thought that I would post the links for anyone else interested that may be experiencing the same problem, but came across this thread and not the others.

Here they are:

[http://forum.tweakxp.com/forum/Topic210621-4-1.aspx](http://forum.tweakxp.com/forum/Topic210621-4-1.aspx)

[http://www.bay-wolf.com/bios.htm#33](http://www.bay-wolf.com/bios.htm#33)

[http://www.dellcommunity.com/supportforums/board/message?board.id=insp_bios&thread.id=41000](http://www.dellcommunity.com/supportforums/board/message?board.id=insp_bios&thread.id=41000)

[http://www.linuxquestions.org/questions/showthread.php?t=570792](http://www.linuxquestions.org/questions/showthread.php?t=570792)

[http://search.euro.dell.com/results.aspx?c=uk&l=en&s=gen&cat=sup&k=Dell+Inspiron+5100+laptop&qmp=12&p=1&subcat=dyd&rf=all&nk=f&sort=K&snpsd=A&ira=False&~srd=False&ipsys=False&advsrch=False](http://search.euro.dell.com/results.aspx?c=uk&l=en&s=gen&cat=sup&k=Dell+Inspiron+5100+laptop&qmp=12&p=1&subcat=dyd&rf=all&nk=f&sort=K&snpsd=A&ira=False&~srd=False&ipsys=False&advsrch=False) (from manndani, see above).


My plan is to burn bootable ISOs of the [A22 BIOS]("http://support.euro.dell.com/support/downloads/format.aspx?releaseid=R65450") and [A32 BIOS]("http://support.euro.dell.com/support/downloads/format.aspx?releaseid=R87515") then shutdown, remove the hard drive and boot from the CDs (I have already tried removing the hdd and running the 7.04 live cd and it worked), first with the A22 BIOS and then with the A32.  Hopefully this will work.  Should my attempts to fix be successful I will post the results.

Also, the warning located at the bottom of this page: [http://www.bay-wolf.com/flashbios.htm](http://www.bay-wolf.com/flashbios.htm) :
Is probably important to at least some users that may be experiencing the same problem, in pertinent part,

[B]&#8220;If you are using Linux on an Inspiron 1100/5100 and you have the Integrated Intel Extreme Graphics chipset (845G chipset), do not upgrade to vesion A22. It has been reported that once you upgrade from A06 to A22, Linux will not see more than 1 MB of shared video RAM. If you have the 16 MB ATI Video care, you will not be affected by this. This is Dell's official response:

*&#8216;Unfortunately, because of the nature of the upgrade from A06 to A22, it is not possible downgrade. This is normal, and is not a glitch. The heart of the issue is that the A22 revision is a totally different format of BIOS than the previous version. So A22 was specially designed to make that change in the old BIOS and it is not currently a reversible process.&#8217;*

As a note, the BIOS Version A06 is a Phoenix BIOS and A22 is a Dell BIOS.&#8221;[/B]

UPDATE -- 7-31-07

The above procedure worked.  Once the HDD was removed I was able to flash from the cd images - first A22 then A32.

---

### Post by mtaschuk on 2007-09-17
I'm a super n00b at dealing with BIOS problems... what do you mean by "flashing" the CD images? 

Also, which is the hard disk on the bottom of the computer? :oops: I've got a Dell Inspiron 5100, same specs as you, same problem except all I want to access my BIOS for is so that I can boot from CD.

---

### Post by drewsimon on 2007-11-14
Weird! I have the exact same problem. I'll try it a bunch more times, then maybe try updating the bios.... But I really don't want to do that.

---

### Post by oilchangeguy on 2007-11-14
flashing the bios is the last thing you want to do. if you're not careful you can create a door stop out of your computer. as for getting into the bios, try pressing and holding the esc key, start the computer while still holding down the key. you should get a keyboard error, and a prompt to enter setup (bios).

---

### Post by JL5100user on 2008-02-14
I just did this tonight!!!!!!! 2/14/08.  The problem seems to be with pheonix BIOS. I did this and got it to work after a week of trying many other suggestions. I had a new RAW drive and the system would not boot to the cd-rom at all.

I tried many other things to try and get into the Bios with no luck.

First I downloaded and burned the ISO image for the A22 BIOS upgrade on another system.

Finally I found on a site that someone recommended to remove the harddrive and reboot with the Burned CD in the drive. My CD-Rom is a little hit and miss at times and finally ran on my third startup.

The BIOS flash started and upgraded it from A06 to A22.

When it restarted the NEW Dell splash showed and had the F2-setup & F12-Temp boot.  Hit F2 and helllloo I was in. Changed my boot order and now loading my new 60GB seagate drive as I type this to you.

Good luck.
Joe

---

### Post by pmsoft on 2008-02-15
I have the same problem: can't access the bios of my Inspiron 5100.

The bios never shows up, even when you have removed the hd.

So I Tried to do the same trick: downloaded the a22 bios update, and removed the HD

But when I boot from the cd, the update of the bios is canceled!

Reason:
I have to clear the administrator password first!!!
(but I cannot access the bios...)

I will put back a ghost image to the hd, so I can use it again. But I will need to attach de HD to an other computer to do so...

---

### Post by JL5100user on 2008-02-15
You may want to try removing the power adapter, battery and CMOS battery. Try to power the system on with all these components removed several times to try and get the BIOS to go to default settings and need to have the internal time and date set.

---

### Post by JL5100user on 2008-02-21
If you do indeed have a BIOS password it may be able to be cleared by removing the laptop battery, the cmos battery (retains cmos settings and cmos passwords), and the power adapter.

Leave the system set for 24 hours and periodically press the power button to drain any residual power that may be in the capacitors.

The system should lose it's set time and date as well as the password.

It should need the time and date reset.

This should work, beyond that you'll have to keep trying to find someone who may have more knowledge on how else to clear the password.

Good Luck

---

### Post by pmsoft on 2008-02-23
There is one problem:

The laptop was protected using an administrator password. Every time the laptop boots,(so not only when you entered the bios)  it asks for this password. According to the Dell documents, if you forget the password, there is no way to retrieve or clear it. In this way the laptop would be of no use if stolen.

So what happens when I remove all batteries, including Cmos battery? I sent an email to Dell to ak them for advise. Maybe they have a solution. If not, I will try the battery trick and pray...

Thanks for your advice.

---

### Post by JL5100user on 2008-03-10
Removing the batteries from the system, especially the CMOS, and allowing the system to set idle for 24-48 hours, perodically pressing the power button will drain all residual power that may remain in the capacitors and should cause the motherboard to lose any information stored (IE: Date, Time & password).

Since my last post I had decided to locate the CMOS battery on mine (5100) and had to completely remove the motherboard from the system only to find the CMOS battery is soldered directly to the motherboard.

The battery is small like a watch battery and the top lead is in plain view. If you intend to go this far the top lead could be cut and let the whole system set for a few hours. resolder the lead and put it back together. I just think this may be a bit to much for some people to do.

I still believe that if the hard drive were removed and you started the system with the A22 BIOS flash CD in the Cd-Rom it would be a better solution. I have been told by a local tech that flashing the BIOS can remove the password.

---

### Post by JL5100user on 2008-03-26
pmsoft

On most desktops ( I know this is a laptop) there is a jumper that if you move it to the opposite side of the pins it resets the CMOS and resets the BIOS to factory default settings.

As far as I know you should not loose the BIOS default settings if you remove the CMOS battery. The CMOS stores temporary information like passwords and date and time, when it looses power it is basically cleared and shouldn't have any password info.

As I said before, removing this battery is quite a task since you have to basically disassemble you laptop to access the CMOS battery. 

Does anyone else have an idea?

Hope this helps.
Joe

---

