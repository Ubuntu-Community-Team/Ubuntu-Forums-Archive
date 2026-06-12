---
title: "Start up problems with Ubuntu7.10"
date: 2007-10-19
forum: General Help
---

### Post by pmeyerslu on 2007-10-19
Hi,

just installed the new Ubuntu7.10 on my DELL INSPIRON 530 procesor Intel® Core™ 2 Duo E6550 2,33 GHz, 4MB memory (1.5 months old)
I installed 3 partitions : 1x Windows Vista (nfts), 1x Shared (fat32), 1x Ubuntu7.10 (ext3).
Problem :
After booting, I get the start menu and I choose the Ubuntu7.10 version. Then I get a black screen with text : Starting Up..... and then :
- sometimes system restarts
- sometimes I get the Ubuntu Logo Screen and in the loading bar only one little orange piece and thats it. Even if I wait a long time, nothing happens. :confused:

Could someone please assist or provide any help.
Tks alot
Paul

---

### Post by krazedkaoz on 2007-10-19
I'm having the same issues, I noticed some kind of usb 5-1 error also.

---

### Post by caldevil on 2007-10-19
Right now its not clear what the error is. Try booting into recovery mode and see if you get any error and paste the error over here.

---

### Post by krazedkaoz on 2007-10-19
I would copy it if it would let me. I had to turn pc off and on and jump back to windows xp.

---

### Post by Wiebelhaus on 2007-10-19
Crtl+Alt+F2 to drop to console ,

Run:

> sudo dkpg-reconfigure xserver-xorg 

Manually choose your configuration , read carefully , three finger salute to restart.

---

### Post by DeanFX on 2007-10-20
> **sx66gns said:**
> Crtl+Alt+F2 to drop to console ,

Run:



Manually choose your configuration , read carefully , three finger salute to restart.

CTRL ALT F2 Doesnt do anything @ the black screen.......ive heard this repeatedly, but it doesn't do anything.  This is harder than installing windows 95 through dos, jesus.. lol

Can someone please help?

---

### Post by pmeyerslu on 2007-10-22
.... my recovery mode boots fine, no problem.
Only problems with the standard mode, I will try Crtl+Alt+F2 and post any error message.

---

### Post by Jimby on 2007-10-22
I too have the same problem.  Using Intel Core 2 Duo e6400, Asus P5B, Radeon x1950pro.
I can get into recovery console and I tried editing the uslpash.conf file but that didnt help.  Its funny, the live CD boots fine.  Looks like I may have to revert back to 7.04.  :(

---

### Post by pmeyerslu on 2007-10-23
:confused::confused::confused::confused:

I started my PC yesterday evening, and it booted without any problem...???
Did a restart, booted again without any problem.

If I get the error again, I will post the error message here.

---

### Post by pmeyerslu on 2007-10-24
I got the message :

[ 153.871117] ata2.00 : exception Emax 0x0 SAct 0x0 Serr 0x0 action 0x2 troz
[ 153.871167] ata2.00 : cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tago cdb 0x1 ata 36 in

So if someone could help.... it would be great

---

### Post by mahousaru on 2007-10-24
> **Jimby said:**
> I too have the same problem.  Using Intel Core 2 Duo e6400, Asus P5B, Radeon x1950pro.
I can get into recovery console and I tried editing the uslpash.conf file but that didnt help.  Its funny, the live CD boots fine.  Looks like I may have to revert back to 7.04.  :(

Did you update the theme after changing the file?

---

### Post by drahomirko on 2007-10-29
Hi guys, I've just get 7.10 release on my compaq and I got some problems with start up. As I turn on comp. it takes around  5-10 minutes  to boot. then everythin's fine and at the end it does not want to neither hibernate nor sleep. All I get after pushing hibernate button is blank black screen and according to controls computer is still running (I hear it do so).I'm confused because of none error messages.PLZ help.Thanx
:):(:confused:

---

### Post by pmeyerslu on 2007-10-29
:confused::confused::confused:

sometimes it happens sometimes not

---

### Post by pmeyerslu on 2007-11-06
I found something....

SATA boot problem, and how I solved it (from tobu)
[http://ubuntuforums.org/showthread.php?t=590931](http://ubuntuforums.org/showthread.php?t=590931)

The fix:
Boot into the Bios configuration (press F2); select "Integrated peripherials", set "Sata mode" to RAID instead of IDE. This has nothing to do with raid, but a different driver that ata_piix will be used, and all will be well.

---

