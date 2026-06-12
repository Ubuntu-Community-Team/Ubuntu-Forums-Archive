---
title: "How to scan with Umax Astra 1220P?"
date: 2007-03-28
forum: General Help
---

### Post by NiksaVel on 2007-03-28
Hey guys... I've never attempted scanning in Linux.. yet... I've been reading around and I've found that SANE has good support for my scanner (Umax Astra 1220P) but I have no idea what to do to actually get to the scanning part...

I've been reading around and I thought I did what I was supposed to

(installed sane, sane-utils, xsane, uncommented umax_pp in dll.conf and entered port 0x378 in umax_pp.conf, set in bios paralel port to ECP+EPP)

but still xsane doesn't detect my scanner which works just fine under windows...


I'm prolly doing somehting wrong and if anyone can help out or point me to a noob how-to I would really appreciate it!


cya
N

---

### Post by NiksaVel on 2007-03-31
Bump

---

### Post by Ghone on 2007-06-10
I'm pretty sure the UMAX Astra 1220p patch does not work with the version of Sane Feisty uses.  You'd need to get sane-backends-1.0.14 then apply the patch, then make and install.

I had no problems under Edgy Eft, but the move to Feisty broke it for me.  It's probably easier to just get a real scanner, but I haven't done that either.

---

### Post by sizzlor on 2007-09-03
dangit! 
i seem to be having the same problem. 

**Ghone**, could you explain what steps i need to take to apply the workaround you described? :confused:
i'm not a total newb, but patching packages is beyond me.

---

### Post by sizzlor on 2007-10-20
**FIXED!**

my UMAX Astra 1220P works 'out of the box' with Gutsy. 
all I had to do was uncomment "umax_pp" in **/etc/sane.d/dll.conf**.

---

### Post by Ptero-4 on 2008-01-30
My astra 1220P (which I didn't use in a while because my computer doesn't have a parallel port, but my sister bought one which does) blinks it's front light and the actual scaning light when I hooked it up to my sisters computer (it happened as soon as I put the power cord in) does it means that the power cord (actually my laptops charger cord since the scanners one went south some time ago) is broken or the scanner is?

---

### Post by NiksaVel on 2008-01-31
maybe the adapter amperage is insufficient or somethin like that....    I don't remamber mine ever blinking anything :)

---

### Post by Ptero-4 on 2008-01-31
But can it damage the adaptor itself.

---

### Post by NiksaVel on 2008-01-31
not an expert...  but I don't think so...   

the device on the other hand is another story...  cuz if you give it too much power, than white smoke comes out :lolflag:

---

