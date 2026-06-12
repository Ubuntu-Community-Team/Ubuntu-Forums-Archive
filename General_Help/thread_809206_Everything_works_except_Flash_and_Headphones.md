---
title: "Everything works except Flash and Headphones"
date: 2008-05-27
forum: General Help
---

### Post by hellmet on 2008-05-27
Ubuntu works wonderfully on my Lenovo Y410 laptop. I'm planning to give it to my father since his current desktop has crumbled to death.  The only reason I'm having to install XP -> 
Flash - Flash overlaps HTML in Ubuntu. I think this is not fixable. 
Sound - No headphone/jack sensing. Sound continues from laptop speakers even after pluggin in external device.

I'd be wonderfully glad if someone would provide a fix (if any) for the second problem. 
Please let me know!!

---

### Post by danwood76 on 2008-05-27
Which flash plugin are you using?

With regards to the headphone issue check that the headphone switch is enabled in the volume control pannel.
If the switches tab doesnt exist you may need to enable it under prefernces.

---

### Post by hellmet on 2008-05-27
I'm using Adobe coz the free flash ain't compatible with few websites. 
There is nothing like 'Headphones' in my volume control. I was able to enable a 'Off-hook' switch, which does nothing though.

---

### Post by danwood76 on 2008-05-27
I did a quick google on your laptop and came up with a possble sound solution:

First open up the alsa config file for editing:
```

sudo gedit /etc/modprobe.d/alsa-base

```
and add the following line to the bottom of the file:
```

options snd-hda-intel index=0 model=fujitsu

```
save and exit, upon a reboot the sound should then work correctly.

What exact issue are you haveing with the adobe flash?

---

### Post by hellmet on 2008-05-27
That was what I had to do to get (any) sound in the first place. Headphone/ Jack sensing doesn't work though.
The issue with Adobe is widely known. Open [www.adobe.com]("http://www.adobe.com") and hover about the menus. Flash overlaps all HTML.

---

### Post by danwood76 on 2008-05-27
Im pretty sure that error is just on the adobe site.
And its quite a funny bug because surely they would have tested with their own site right?
Ive got flash 10 beta going and the bug is still there too.

Not sure what to do about your audio, there are different options you could try with alsa though I'm not sure with your audio card.

You could try something like:
```

options snd-hda-intel index=0 model=3stack

```
I have no idea how your sound card is setup though so its a bit hit and miss.

---

### Post by hellmet on 2008-05-29
Tried that before. Didn't work. 
The IEC958 switch enabled the red laser light for sound. I don't know what that is though. But headphone sense is yet to work.

---

### Post by danwood76 on 2008-05-29
IEC958 is S/PDIF, so its digital audio and the light is the fiber optic output.

There are several other options you could try, I think that your sound card is supported by alsa its just the options are wrong.
```

options snd-hda-intel index=0 model=lenovo

```
```

options snd-hda-intel index=0 model=auto

```

---

### Post by hellmet on 2008-05-30
Btw, the adobe flash thing is not just confined to their site. This problem is noticeable on all sites with flash

---

### Post by danwood76 on 2008-05-30
I dont think so.
Google video for example has html over the flash videos and it works. (even with CSS)

To make the sites viewable you could use flash block, most flash animations are just adverts anyway.

---

### Post by jalanbuntu on 2008-07-01
Got stuck with some problem with the jack output :(

---

