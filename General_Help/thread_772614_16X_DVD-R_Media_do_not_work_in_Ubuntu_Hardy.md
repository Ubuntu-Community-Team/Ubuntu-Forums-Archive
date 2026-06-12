---
title: "16X DVD-R Media do not work in Ubuntu Hardy"
date: 2008-04-28
forum: General Help
---

### Post by ibookdb on 2008-04-28
Ubuntu burns DVDs fine on 8X DVD-R media but all applications (Brasero, GnomeBaker, K3B, Nautilus) fail to burn on 16X DVD-R media.

I tried two different brands (one of them was generic 16X media - not tried in Win, the other was Philips 1-16X - these work fine on the same computer in Windows).

The only software with a meaningful error is K3B which says "OPC Failed". The rest just say "I/O Error"

The computer is a Thinkpad R51 with a 2.4X DVD Burner. The same problem was occuring in 7.10 before I upgraded to 8.04 over the weekend and tried again hoping it would work. I'm out of 8X media now and I can't seem to find any in stores either. So any help in getting this to work is appreciated.

Thanks

---

### Post by russo.mic on 2008-04-28
Well, are you manualy setting the speed in these burning apps?  It would seem to me that the media is failing because your dvd burner is not properly being controlled.  I would set it to burn as slow as possible, and see if that fixes it, and maybe increase the speed from there to see when it starts failing.

Russo

---

### Post by ibookdb on 2008-04-28
> **russo.mic said:**
> Well, are you manualy setting the speed in these burning apps?  It would seem to me that the media is failing because your dvd burner is not properly being controlled.  I would set it to burn as slow as possible, and see if that fixes it, and maybe increase the speed from there to see when it starts failing.

Russo

Burning at 1X also does not work.

---

### Post by omriasta on 2008-05-01
Also have a thinkpad R61...same issue. Burning works fine on Windows and worked fine in Gutsy. I couldn't find anywhere for setting or preferences in the new burning apps. It just fails.....

---

### Post by omriasta on 2008-05-01
Sorry for posting before looking at other forums.
Simple Fix:
sudo gedit /boot/grub/menu.lst
add all_generic_ide at the end of the line:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b335618a-0043-4542-b1f3-52f5e9a01d96 ro quiet splash all_generic_ide
That did it for me!

---

### Post by yamawho on 2008-05-01
Does the media in question actually burn at 16x in windows ?

May be a hardware issue, burner doesn't like the media and burns disk at 8x instead.

FYI any DVD burned at speeds over 8x have more errors.

Same for CD's but the speed is 16x.

After much testing with Plextools this is a good rule of thumb.

---

### Post by ibookdb on 2008-05-02
> **yamawho said:**
> Does the media in question actually burn at 16x in windows ?

May be a hardware issue, burner doesn't like the media and burns disk at 8x instead.

FYI any DVD burned at speeds over 8x have more errors.

Same for CD's but the speed is 16x.

After much testing with Plextools this is a good rule of thumb.

The burner is 2.4X so all DVDs burn at 2.4X. Just that 16X media do not work . I still have to try the all_generic option. I'll try it when I get the chance maybe next week.

---

### Post by Joe Beam on 2008-05-15
Any solution for this? 

My discs were burning fine under gutsy, but I get this error under hardy (using K3B)...

```

Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=100h failed with SK=5h/ASC=A8h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/scd1: flushing cache
/dev/scd1: updating RMA
/dev/scd1: closing disc

```

dmesg
[  152.646899] cdrom: This disc doesn't have any tracks I recognize!

Burner...
'PIONEER ' 'DVD-RW  DVR-115D' 

Disc Brand...
memorex DVD-R 16X


The all_generic_ide option did not work for me.

Brasero errors out and so does gnomebaker.

---

### Post by ibookdb on 2008-05-16
Ooh, for me 16x media didn't work in gutsy either. I was hoping upgrading to hardy would fix it.

---

### Post by Seventh Reign on 2008-05-16
I have a Spindle of 100 16x DVD+R's, of which I've burnt close to 40.  They all burn perfectly except it only burns at 4.10x no matter what speed I choose.  The Burner is rated at 20x.

Of course 4x is 8 Times faster than my Windows system burns.  My XP wont burn faster than .5x!!!

And I wont use ANY media other than Maxell.  CD/DVD whatever .. if it isnt Maxell I'm not wasting my money.  I've only wasted one DVD+R out of about 200 .. and that was my own fault not the Discs.

I love H.H. :-)

---

### Post by Joe Beam on 2008-05-18
It's burning again. I didn't do anything that I know of.

Oh yeah, I forgot to mention that I would get those errors on write simulations as well as writes. If that makes a difference.

I like when things fix themselves. :)

---

### Post by JustinTX on 2008-05-19
> **Joe Beam said:**
> Any solution for this? 

My discs were burning fine under gutsy, but I get this error under hardy (using K3B)...

```

Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=100h failed with SK=5h/ASC=A8h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/scd1: flushing cache
/dev/scd1: updating RMA
/dev/scd1: closing disc

```

dmesg
[  152.646899] cdrom: This disc doesn't have any tracks I recognize!

Burner...
'PIONEER ' 'DVD-RW  DVR-115D' 

Disc Brand...
memorex DVD-R 16X


The all_generic_ide option did not work for me.

Brasero errors out and so does gnomebaker.

This is still happening to me. Mine has not magically fixed itself. I even swapped out burners thinking the original had died. I also reinstalled Hardy from the media instead of dist-upgrade. I did a fresh install of Gutsy, downloaded Hardy, burned it, installed it, and now I cannot burn.

Update: Seems to work now that I've rearranged the drives on the IDE channel. Before DVD-ROM - Primary Master/DVD-RW - Primary Slave, now DVD-RW - Primary Master/No DVD-ROM. Not sure why it made a difference exactly.

---

### Post by Joe Beam on 2008-05-19
broke again.

same error as before.

edit> 

not sure what's going on. I restarted with  an empty disc in the tray and now k3b is burning again.

This is hit or miss. If the simulation doesn't error out right away, the next write works. Helps me from making to many coasters.

---

