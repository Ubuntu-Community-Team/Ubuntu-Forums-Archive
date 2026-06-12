---
title: "VCD Playing Problem"
date: 2006-11-24
forum: General Help
---

### Post by harishgayatri on 2006-11-24
I am using Ubuntu 6.10 with totem-Xine installed.
I am not able to Play VCD´s With totem,gxine.Vlc.

Totem gives me the following ERROR.

Totem could not play this media (Video CD) although a plugin is present to handle it.
You might want to check that a disc is present in the drive and that it is correctly configured.


Please Help.
Thanks in Advance...

---

### Post by balan on 2006-11-25
I wish someone could answer your question because I've searched everywhere for a solution & can't find one that works. If you do a google search you will find that there are many, many people with the same problem. Some say use VLC, Kaffeine, xine etc but nothing seems to work for me.
I can play just about every other multimedia format (DVD's, DivX, Xvid, real, wmv etc..etc..)but for some inexplicable reason not VCD's.
I really want to dump windows for good but the inability to play something as simple as VCD's is baffling & unbelievable.

---

### Post by kwidzin on 2006-12-12
gconfeditor -> gnome -> volume_manager -> autoplay_vcd_command -> totem%m <- changing for: totem vcd:// and vcd running great ;-)

---

### Post by nlz on 2008-02-27
or: gxine vcd://

strange stuff isn't it? When you just run xine and select VCD, it makes problems, but  if you try if directly, no problem..

Now i can delete the 50 MB on codecs i just downloaded ghegehghe

---

### Post by ellalan on 2008-02-28
Hi NLZ
I am a newbe and struggling to play VCD, can you please help me how to install the gxine and where do I make the entries you have stated, your help is much appreciated.

---

### Post by kpkeerthi on 2008-02-28
mplayer plays VCD fine. Launch mplayer, right-click -> Open disc -> VCD

[Install Instructions]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html")

---

### Post by ellalan on 2008-02-28
Hi nlz
I have solved my VCD problem by entering in Terminal "apt-get install ubuntu-restricted-extras"
Thank you.

---

### Post by nlz on 2008-02-29
hi ellalan,
In my experience, this doesn't cover all VCD's. VCD's is a kind of dumbster format for many different codecs. I like gxine just because of the nice and stable engine which is *in my opinion * much better then totem and the gstreamer plugins.

You can try xine by starting synaptic (system>administration>synaptic), and then search gxine. Then you good to go!

---

### Post by ellalan on 2008-02-29
Hi nlz
I have gxine working well in my pc while others failed, Thank you.

---

