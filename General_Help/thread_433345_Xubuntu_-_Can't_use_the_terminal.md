---
title: "Xubuntu - Can't use the terminal"
date: 2007-05-04
forum: General Help
---

### Post by itchanddino on 2007-05-04
I've installed feisty using upgrade, fresh install on the livecd and a fresh install on the alt. cd.  Each time, I zeroed the drive.  Whenever I try to launch the terminal, my screen goes black and it brings me back to the login screen.  Is there any fix for this?  Thanks!

---

### Post by Pox on 2007-05-04
Try hitting Alt+F2 and running xterm - see if that works.

If it does, run 
```
xfterm4 2> ~/terminalerrors.txt
```

It'll probably crash. However, we'll have a record of any errors.

Open up the file manager to your home folder and view terminalerrors.txt, then post the contents here and we'll have a look.

---

### Post by Eoghanalbar on 2007-05-05
Pox, I got exactly the same problem.
Followed your directions, got this:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "o"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)
Warning:          No symbols defined for <FK16> (keycode 121)
Warning:          No symbols defined for <FK17> (keycode 122)
Warning:          No symbols defined for <KPDC> (keycode 123)
Warning:          No symbols defined for <XFER> (keycode 129)
Warning:          No symbols defined for <I02> (keycode 130)
Warning:          No symbols defined for <NFER> (keycode 131)
Warning:          No symbols defined for <I04> (keycode 132)
Warning:          No symbols defined for <AE13> (keycode 133)
Warning:          No symbols defined for <I06> (keycode 134)
Warning:          No symbols defined for <I07> (keycode 135)
Warning:          No symbols defined for <I08> (keycode 136)
Warning:          No symbols defined for <I09> (keycode 137)
Warning:          No symbols defined for <I0A> (keycode 138)
Warning:          No symbols defined for <I0B> (keycode 139)
Warning:          No symbols defined for <I0C> (keycode 140)
Warning:          No symbols defined for <I0D> (keycode 141)
Warning:          No symbols defined for <I0E> (keycode 142)
Warning:          No symbols defined for <I0F> (keycode 143)
Warning:          No symbols defined for <I10> (keycode 144)
Warning:          No symbols defined for <I11> (keycode 145)
Warning:          No symbols defined for <I12> (keycode 146)
Warning:          No symbols defined for <I13> (keycode 147)
Warning:          No symbols defined for <I14> (keycode 148)
Warning:          No symbols defined for <I15> (keycode 149)
Warning:          No symbols defined for <I16> (keycode 150)
Warning:          No symbols defined for <I17> (keycode 151)
Warning:          No symbols defined for <I18> (keycode 152)
Warning:          No symbols defined for <I19> (keycode 153)
Warning:          No symbols defined for <I1A> (keycode 154)
Warning:          No symbols defined for <I1B> (keycode 155)
Warning:          No symbols defined for <K59> (keycode 157)
Warning:          No symbols defined for <I1E> (keycode 158)
Warning:          No symbols defined for <I1F> (keycode 159)
Warning:          No symbols defined for <I20> (keycode 160)
Warning:          No symbols defined for <I21> (keycode 161)
Warning:          No symbols defined for <I22> (keycode 162)
Warning:          No symbols defined for <I23> (keycode 163)
Warning:          No symbols defined for <I24> (keycode 164)
Warning:          No symbols defined for <I25> (keycode 165)
Warning:          No symbols defined for <I26> (keycode 166)
Warning:          No symbols defined for <I27> (keycode 167)
Warning:          No symbols defined for <I28> (keycode 168)
Warning:          No symbols defined for <I29> (keycode 169)
Warning:          No symbols defined for <K5A> (keycode 170)
Warning:          No symbols defined for <I2B> (keycode 171)
Warning:          No symbols defined for <I2C> (keycode 172)
Warning:          No symbols defined for <I2D> (keycode 173)
Warning:          No symbols defined for <I2E> (keycode 174)
Warning:          No symbols defined for <I2F> (keycode 175)
Warning:          No symbols defined for <I30> (keycode 176)
Warning:          No symbols defined for <I31> (keycode 177)
Warning:          No symbols defined for <I32> (keycode 178)
Warning:          No symbols defined for <I33> (keycode 179)
Warning:          No symbols defined for <I34> (keycode 180)
Warning:          No symbols defined for <K5B> (keycode 181)
Warning:          No symbols defined for <K5D> (keycode 182)
Warning:          No symbols defined for <K5E> (keycode 183)
Warning:          No symbols defined for <K5F> (keycode 184)
Warning:          No symbols defined for <I39> (keycode 185)
Warning:          No symbols defined for <I3A> (keycode 186)
Warning:          No symbols defined for <I3B> (keycode 187)
Warning:          No symbols defined for <I3C> (keycode 188)
Warning:          No symbols defined for <K62> (keycode 189)
Warning:          No symbols defined for <K63> (keycode 190)
Warning:          No symbols defined for <K64> (keycode 191)
Warning:          No symbols defined for <K65> (keycode 192)
Warning:          No symbols defined for <K66> (keycode 193)
Warning:          No symbols defined for <I42> (keycode 194)
Warning:          No symbols defined for <I43> (keycode 195)
Warning:          No symbols defined for <I44> (keycode 196)
Warning:          No symbols defined for <I45> (keycode 197)
Warning:          No symbols defined for <K67> (keycode 198)
Warning:          No symbols defined for <K68> (keycode 199)
Warning:          No symbols defined for <K69> (keycode 200)
Warning:          No symbols defined for <K6A> (keycode 201)
Warning:          No symbols defined for <I4A> (keycode 202)
Warning:          No symbols defined for <K6B> (keycode 203)
Warning:          No symbols defined for <K6C> (keycode 204)
Warning:          No symbols defined for <K6D> (keycode 205)
Warning:          No symbols defined for <K6E> (keycode 206)
Warning:          No symbols defined for <K6F> (keycode 207)
Warning:          No symbols defined for <HKTG> (keycode 208)
Warning:          No symbols defined for <K71> (keycode 209)
Warning:          No symbols defined for <K72> (keycode 210)
Warning:          No symbols defined for <AB11> (keycode 211)
Warning:          No symbols defined for <I54> (keycode 212)
Warning:          No symbols defined for <I55> (keycode 213)
Warning:          No symbols defined for <I56> (keycode 214)
Warning:          No symbols defined for <I57> (keycode 215)
Warning:          No symbols defined for <I58> (keycode 216)
Warning:          No symbols defined for <I59> (keycode 217)
Warning:          No symbols defined for <I5A> (keycode 218)
Warning:          No symbols defined for <K74> (keycode 219)
Warning:          No symbols defined for <K75> (keycode 220)
Warning:          No symbols defined for <K76> (keycode 221)
Warning:          No symbols defined for <I5E> (keycode 222)
Warning:          No symbols defined for <I5F> (keycode 223)
Warning:          No symbols defined for <I60> (keycode 224)
Warning:          No symbols defined for <I61> (keycode 225)
Warning:          No symbols defined for <I62> (keycode 226)
Warning:          No symbols defined for <I63> (keycode 227)
Warning:          No symbols defined for <I64> (keycode 228)
Warning:          No symbols defined for <I65> (keycode 229)
Warning:          No symbols defined for <I66> (keycode 230)
Warning:          No symbols defined for <I67> (keycode 231)
Warning:          No symbols defined for <I68> (keycode 232)
Warning:          No symbols defined for <I69> (keycode 233)
Warning:          No symbols defined for <I6A> (keycode 234)
Warning:          No symbols defined for <I6B> (keycode 235)
Warning:          No symbols defined for <I6C> (keycode 236)
Warning:          No symbols defined for <I6D> (keycode 237)
Warning:          No symbols defined for <I6E> (keycode 238)
Warning:          No symbols defined for <I6F> (keycode 239)
Warning:          No symbols defined for <I70> (keycode 240)
Warning:          No symbols defined for <I71> (keycode 241)
Warning:          No symbols defined for <I72> (keycode 242)
Warning:          No symbols defined for <I73> (keycode 243)
Warning:          No symbols defined for <I74> (keycode 244)
Warning:          No symbols defined for <I75> (keycode 245)
Warning:          No symbols defined for <I76> (keycode 246)
Warning:          No symbols defined for <I77> (keycode 247)
Warning:          No symbols defined for <I78> (keycode 248)
Warning:          No symbols defined for <I79> (keycode 249)
Warning:          No symbols defined for <I7A> (keycode 250)
Warning:          No symbols defined for <I7B> (keycode 251)
Warning:          No symbols defined for <I7C> (keycode 252)
Warning:          No symbols defined for <I7D> (keycode 253)
Warning:          No symbols defined for <I7E> (keycode 254)
Warning:          No symbols defined for <I7F> (keycode 255)
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xscreensaver: 17:55:12: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 17:55:12: 0: for window 0x1000003 (Thunar / Thunar)
xscreensaver: 17:55:20: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 17:55:20: 0: for window 0x1c000c0 (opera / Opera)
xscreensaver: 18:01:11: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 18:01:11: 0: for window 0x1000003 (Thunar / Thunar)

```

---

### Post by vash469 on 2007-05-05
i am having the same problem i just downloaded the ubuntu termainal to get around it but it there a way to fix this yet ????

---

### Post by ridgeland on 2007-05-06
I've got the same problem.
I don't know what the menu runs. But from the menu Applications -> Accessories -> Terminal the system blanks out and goes back to the login screen.
I have Xubuntu installed on two PCs.  On the newer PC I have the 'regular' version of Xubuntu and the terminal window works.  On the older PC (1997 model) I have Xubuntu - alternative installed. There I get the crash out to login each time i ask for the terminal.
If I use Thunar and go to /usr/bin/xfce4-terminal and say execute - I get the crash out to the login screen.  If in Thunar I go to /usr/bin/xterm I get a terminal window.  I gave this a right click and put it on the desktop.  So at least I have a simple fix but xterm is not nearly as sexy a window, no neat color options.
I also installed Icewm.  With the IceWM desktop the terminal window works fine.  I get to pick the colors and such.
What gives?  I'll explore some more.  
Xterm is an easy fix to have a terminal window until something better shows up.  Just Thunar and right click it to the desktop.

---

### Post by ridgeland on 2007-05-07
More observations.
I installed Xubuntu-Desktop from another CD.  My old PC still crashes when trying to use the terminal just like with Xubuntu-Alternate.  Again the simple fix was to put xterm on the desktop.

This old PC also has the problem of incomplete shutdown. Such as discussed in the thread about 'incomplete shutdown'
[http://ubuntuforums.org/showthread.php?t=359190](http://ubuntuforums.org/showthread.php?t=359190)

I don't know if or how the two problems are related but I suspect this is only an issue for very old equipment. My old PC is a 200MHz Pentium MMX, cpu family 5.  The BIOS is from around 1997 or earlier.

My antique PC does better with IceWM.  It's harder to setup the menus but IceWM is better suited to such old equipment.

---

### Post by itchanddino on 2007-05-13
I found a fix for it on the forums:

[http://ubuntuforums.org/showthread.php?t=417661](http://ubuntuforums.org/showthread.php?t=417661)

---

### Post by ridgeland on 2007-05-13
Thank you itchanddino.
The note from TheForkOfJustice about changing default depth from 24 to 16 solved my issue with the terminal causing a crash.
Thanks for following up by posting the solution you found.

---

### Post by pandan on 2007-05-18
I also had this problem but it was fixed after I installed all updates.

---

