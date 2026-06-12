---
title: "output jack in the docking station is not working/recognized"
date: 2007-10-23
forum: General Help
---

### Post by SONYVAIOVGN-FZ18M on 2007-10-23
Hello, 

Sorry for my english, I'm french.

The problem:

I have a sony vaio VGN FZ 18 M. Windows and ubuntu gutsy gibbon, dual boot. 

output jack does not mute internal speakers,
output jack in the docking station is not working/recognized,
internal speakers are working.

everything is ok under windows, headphones and speakers. 

2.6.22-14-386


alsa mixer version 1.0.14

Card: hda intel, chip: sigma tel STAC9872AK

lspci grep audio:

Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

asoundconf list
Names of available sound cards:
Intel

grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: SigmaTel STAC9872AK
/proc/asound/card0/codec#1:Codec: Conexant ID 2c06

 lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 
00:1b.0 0403: 8086:284b (rev 03)

What should I do?

Thanks, 

Yann from Paris.

---

### Post by Fayte2071 on 2007-11-24
I'm going to have to bump this. This is the same exact problem I'm having with my sony vaio, and it's really ticking me off now. Everything works fine in windows, but the headphone jack doesn't work in ubuntu gutsy. What can i do? This is really irritating me.

---

### Post by pascalc on 2007-11-24
same problem with the same sound chipsert on a Sony Vaio VGN-FZ21E

---

### Post by gamermann on 2007-11-26
I have the same problem in a vaio vgn-fz21e also. 
I read this post [http://ubuntuforums.org/showthread.php?t=76307](http://ubuntuforums.org/showthread.php?t=76307), but it didnt help...
 Let's wait if some one knows how to fix it.

---

### Post by Neonjack on 2007-11-27
Same here!  VAIO VGN-FZ14QE.
Those f***ers at Sony!!!  Damn!  Also, video card not recognized... AND S VIDEO not working.
Woo-hoo....

---

### Post by Fayte2071 on 2007-11-27
Can someone who's linux savvy help us? please?

---

### Post by dpj23 on 2007-11-27
I have the same problem with my Dell (D610)... I never considered it the end all of problems and since I'm not running Microsoft would gladly plug in the speakers to the laptop instead of the docking station...   However, now that the subject has been tabled, I would be interested in seeing what answers come up...  I'm sorry that I don't have the answer... But share in your interest...

---

### Post by bigbrovar on 2007-12-05
mehn i just joined the club.. brightness dont work  on my system too.. now i dont know what do do my last lappy was 100% ubuntu compliant.. but i wanted to be savy and i wwent to by sony vaio fz21e now i feel like a punk.. is there anybody out there with a solution that could help?

---

