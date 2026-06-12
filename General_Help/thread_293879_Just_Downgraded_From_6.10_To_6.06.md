---
title: "Just Downgraded From 6.10 To 6.06"
date: 2006-11-05
forum: General Help
---

### Post by Sethro on 2006-11-05
hi everyone 

I just downgraded from Ubuntu 6.10 to Ubuntu 6.06 and so far I noticed that Firefox is amazing much better in Ubuntu 6.06. Also Open Office looks so much better in 6.06 and fonts looks alot better too. But the main reason was in Ubuntu 6.10 I had a huge problem with the fan always on. But now the fan has slown down alot and I was woundering can I make it even quieter??

Thanks Guys

---

### Post by Sethro on 2006-11-05
No.. no   nobody??  lol

---

### Post by tortus on 2006-11-05
What steps did you take to downgrade? I want to downgrade back to 6.06 too, but I'm not really sure how to do it.

---

### Post by Azakus on 2006-11-05
Why did you downgrade really? The fonts thing can be taken care of with a very easy fix.

sudo gedit ~/.fonts.conf
Copy this and paste:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

---

### Post by Sethro on 2006-11-05
Well what I did was I downloaded Ubuntu 6.06 and did a backup of all my documents and just did a fresh install of everything. But guys... how about the whole powersaver thing? Can anybody help me out with it?


Thanks

---

### Post by mark2741 on 2006-11-05
Sorry to jump in on this thread but....

What exactly does the edit you list below for the .fonts file do? I'd like clearer fonts overall and this is the first time I've seen the stuff below mentioned. Is it safe to do this for every Edgy install?

Thanks,

mark



> **Azakus said:**
> Why did you downgrade really? The fonts thing can be taken care of with a very easy fix.

sudo gedit ~/.fonts.conf
Copy this and paste:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

---

### Post by lawina on 2006-11-06
> **Sethro said:**
> 

 But the main reason was in Ubuntu 6.10 I had a huge problem with the fan always on. But now the fan has slown down alot and I was woundering can I make it even quieter??



Are you using a laptop? In that case you might need a laptop cooler(USB)!

---

### Post by juve on 2006-11-06
If you have a powersaving/fan-speed or a font problem, you should probably make your thread more clear.
"Just Downgraded From 6.10 To 6.06" sounds like a general topic and not everybody (i.e. people who know about powersaving/fonts) will read it. I'd open a new thread (after doing some search first ;))

---

### Post by Hemmer on 2006-11-06
you firefox is much better in 6.06. which version is this? 1.5 or 2.0?

because I'm running firefox 2.0 on edgy and its brilliant. also havn't found any reason to downgrade at all... :D

---

### Post by doobit on 2006-11-06
Fan speed and power are part of the acpi package, I think. On some computers, there is both an APM and and ACPI capability so you need to tell Ubuntu what to choose on startup. There shouyld be a message that pops up very quickly as you boot up that will tell you. You won't be able to see it if you have "quiet" enabled in your bootloader, but you should be able to see it in dmesg, or your bootlogs. Mine told be that I needed to put acpi=force in the linux boot command line in GRUB. Once I did that, all of the acpi functions worked correctly.

---

### Post by cmost on 2006-11-06
> **Azakus said:**
> Why did you downgrade really? The fonts thing can be taken care of with a very easy fix.

sudo gedit ~/.fonts.conf
Copy this and paste:
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>


You call this a "very easy fix"?  Yeah, I'm sure doing this was totally obvious to everyone, especially newbies.  ](*,)

---

### Post by Sethro on 2006-11-06
> **cmost said:**
> You call this a "very easy fix"?  Yeah, I'm sure doing this was totally obvious to everyone, especially newbies.  ](*,)

LOL:mrgreen:

---

### Post by floke on 2006-11-16
Has anybody tried this? Does it work?
OOo fonts in Edgy are a bit pants.
S

---

### Post by matthew871 on 2007-06-28
> **mark2741 said:**
> Sorry to jump in on this thread but....

What exactly does the edit you list below for the .fonts file do? I'd like clearer fonts overall and this is the first time I've seen the stuff below mentioned. Is it safe to do this for every Edgy install?

Thanks,

mark

idk, made my Ubuntu 7.04 fonts look too sharp and ugly. :P

---

