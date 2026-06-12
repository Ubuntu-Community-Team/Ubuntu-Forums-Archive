---
title: "Totem WMV"
date: 2005-06-18
forum: General Help
---

### Post by keybreckaba on 2005-06-18
When i try to play a wmv file it will play the sound but no video what is wrong and how can i fix it. 
Thanks

---

### Post by Evoreth on 2005-06-18
Have you installed the codecs, especially w32codecs?
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by keybreckaba on 2005-06-18
yes i have w32codecs installed

---

### Post by ssck on 2005-06-19
sorry to barge in like this ... i have an issue with totem-xine where there are certain wmv files that i play which has video and sound, but some of them with video but no sound ??? has anyone faced this issue ?

---

### Post by bored2k on 2005-06-19
[QUOTE=ssck]sorry to barge in like this ... i have an issue with totem-xine where there are certain wmv files that i play which has video and sound, but some of them with video but no sound ??? has anyone faced this issue ?[/QUOTE]
 Download gxine and try running it with that. Sometimes I notice BAD playback with totem and vlc (my favorite for good encoded videos) but flawless playback with gxine. * When you install, it won't have a menu entry.

---

### Post by ssck on 2005-06-19
[QUOTE=bored2k]Download gxine and try running it with that. Sometimes I notice BAD playback with totem and vlc (my favorite for good encoded videos) but flawless playback with gxine. * When you install, it won't have a menu entry.[/QUOTE]


need to ask though ... where do i download the software ? it is not in synaptic.

appreciate your help.

thanks

---

### Post by rider343 on 2005-06-19
your sources.list have the extra repos?

---

### Post by ssck on 2005-06-20
[QUOTE=rider343]your sources.list have the extra repos?[/QUOTE]

hi, 

i managed to install gxine.

thanks.

---

### Post by Bandit on 2005-06-20
Here is why WMV will not play with the latest version of Xine.
SImple, you can read this at xine's website.
They (due to legal reasons) removed WMV capabilities.
I suppose you can edit the source code by hand to enable it, unless they totaly removed the code.
Good news is the latest version of xine will still play DVD's and it uses 10% CPU on my 2.1Ghz AthlonXP system. (You still need libdvdcss for Encrypted DVD's)
Cheers,
Joey

---

### Post by desdinova on 2005-06-20
As I recall there are two versions of WMV, some are protected in some way and hence why you can't play them...

---

### Post by xbilly on 2005-06-20
Hey. I am having video problems too and I noticed this.

Open the video up in XINE. If you have XINE installed... do it by right clicking the file and selecting Open with 'xine" or "Open with other Application". The video will most likely play only the audio but no image or scrambly. let it do this, but while it is "playing" do the same thing again with the file. By opening two instences of the video at the same time in XINE, it seems to work for the second instence. I have NO idea why.

billy

---

