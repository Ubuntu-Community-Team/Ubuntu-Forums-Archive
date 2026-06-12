---
title: "DVD PlayBack"
date: 2005-03-28
forum: General Help
---

### Post by clb137 on 2005-03-28
Hi Anyone,

Having upgraded from warty where everthing was fine,  I now find that my dvd playback is jerky and there is no sound.

I know that there is a lot threads threads on this, however none is specific.  the guide is for warty and therefore it does not work in 'Hoary'

Has anyone managed to get smooth playback and sound working for DVD playback working in 'Hoary'?  If so how please can you let me know,  

I know that Killall esd works fro the sound  but that is only a halg measure

and hdparm -1 for the dma for the cd/dvd drive.

can some tell me how to make this happen automatically please

thanks 

clinton

---

### Post by wmcbrine on 2005-03-28
[http://ubuntuforums.org/showpost.php?p=105749&postcount=3](http://ubuntuforums.org/showpost.php?p=105749&postcount=3)

To get rid of esd, you can just uncheck "Enable sound server startup" in System, Preferences, Sound, General. If you do, you might also want to change to ALSA under Multimedia Systems Selector; app-specific config may be required in some cases as well.

---

### Post by lukem on 2005-03-28
Using totem-xine I haven't had any problems with commercially produced dvds.  The ones I recorded will not work however.  Both worked in warty though.  Also I don't have to kill esd to get sound.  The how-to for warty was fabulous and I hope someone can put one together for hoary as well.

---

### Post by nehalem on 2005-03-29
I get sound it totem but playback is incredibly jerky.  In VLC it's jerky too.

What's up?

Is it just the sound or something else too?

---

### Post by clb137 on 2005-03-29
[QUOTE=nehalem]I get sound it totem but playback is incredibly jerky.  In VLC it's jerky too.

What's up?

Is it just the sound or something else too?[/QUOTE]


hi 

Just edit the folowing file /etc/hdparm.conf 

with

/dev/hda {
        mult_sect_io = 16
        dma = on
}

look for the line /dev/cdrom or something simular and replace it with the above and remove the other 2 lines, remember to reomve the # so the lines are read a code

good luck

clinton

---

