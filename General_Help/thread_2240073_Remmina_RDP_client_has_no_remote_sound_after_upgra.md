---
title: "Remmina RDP client has no remote sound after upgrade to 14.04.1 LTS"
date: 2014-08-17
forum: General Help
---

### Post by fizikz on 2014-08-17
Remmina (v 0.9.99.1) no longer plays remote sound after a system upgrade from Ubuntu 12.04 to 14.04.1. The computer I connect to, running Windows Server 2008  R2, shows a red X on the audio icon and has the message "No Audio Output Device is installed." Please help! This is an unpleasant regression from something that was working well before. Incidentally, are there any other RDP clients with NLA support that might be recommended?

---

### Post by fizikz on 2014-08-18
So far the patch in post #7 [here]("https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1215477") is the only solution I've found, but I'm not sure how to apply it. Hard to believe this problem has gone unsolved for a year.

---

### Post by fizikz on 2014-08-18
I'd be willing to try manually applying the patch and compiling Remmina from source. I downloaded the source from here: [https://github.com/FreeRDP/Remmina/downloads](https://github.com/FreeRDP/Remmina/downloads) 
The changes to rdp_plugin.c from the patch file were easy enough to make, although they did not correspond to exactly the same line numbers (starting on line 780 vs 794 in patch file).

Now I'm not sure how to actually compile this. There is one README in the root directory, and then other README files in each of the subdirectories, plus INSTALL files... 

I tried doing the usual "./configure;  make;  sudo make install" but there is no configure file to begin with. 

Any help with this?

---

### Post by q-brian on 2014-08-29
When will the patch be integrated into the updates?

---

### Post by fizikz on 2014-08-29
I have no idea when the fixes will be reflected in the package available in the Ubuntu repository, but currently several people are working on bug fixes. If you're adventurous you can follow [this new wiki]("https://github.com/FreeRDP/Remmina/wiki/Compile-on-Ubuntu-14.04") entry to compile the latest version of Remmina from source. Note that it may have bugs as it is still in active development, but at least the sound does work.

---

### Post by keith-finnie on 2015-03-03
[COLOR=#333333][FONT=UbuntuRegular]I had the same problem using Ubuntu 14.04. Tried with Remmina, 2XRDP and rdesktop - no audio with any of them. Looked around and found reference to the "esound" package on the 2X site.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Installed it using "sudo apt-get install esound" , and in response got the message:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Note, selecting 'pulseaudio-esound-compat' instead of 'esound'[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]... but it installed and worked with Remmina with no further fuss (make sure sound is turned on in the "Advanced" tab).[/FONT][/COLOR]

---

