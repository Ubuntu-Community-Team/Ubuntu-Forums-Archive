---
title: "No sound from Line Out"
date: 2021-05-30
forum: General Help
---

### Post by rustyshackleford12 on 2021-05-30
Hi all, new to Linux and need help with audio issue... 

I'm running 21.04 on an Intel based Gigabyte GA-H170 gaming motherboard,  I can get sound out of the Line Out on front side of chassis, but  cannot get sound out of rear Line Out. I know they both work, I'm dual  boot with Win10, and works fine in that OS. Have tried changing in  settings and no matter what, cant get sound from rear Line Out. Config  is, Speaker connected to Front Line Out, Headset connected to rear Line  Out & Mic In. 

I'd appreciate any suggestion as everything else is working very well in  21.04, only this minor issue left to resolve and I'm stumped...

---

### Post by dragonfly41 on 2021-05-30
There are other cases if you broaden your search net ..

[https://askubuntu.com/questions/1210690/no-sound-from-line-out-in-ubuntu-19-10-on-alc1220](https://askubuntu.com/questions/1210690/no-sound-from-line-out-in-ubuntu-19-10-on-alc1220)

---

### Post by rustyshackleford12 on 2021-05-30
Thanks [**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878")... I neglected to mention I did search many other forums, blogs etc... This is my last resort.

In settings, the only options that appear for audio output are - 
[LIST]
[*]Digital Audio (S/PDIF) - Built-in Audio         --  Which I'm not connected to
[*]HDMI/DisplayPort 2  -- for my monitor, which works fine
[*]Headphones - Built-in Audio   --  front panel line out for my speaker, which works as well
[/LIST]

I'm missing the rear panel Line out option. I had already tried alsmixer, as suggested int he link you provided, and it does not provide option to interact with that output either... As I said, all this works fine in Windows, so there's something I'm missing n Ubuntu that I cannot seem to find a way to enable or interact with that output...

Any further assistance would be greatly appreciated.

---

### Post by dragonfly41 on 2021-05-30
This is pure guesswork on my part based on the clues I have read.
But if it works in Windows 10, then if the theory in above link is valid ...

   Collision between a Windows Realtek driver and a Linux HDA driver   

then I wonder if you might get non conflicting results using Windows 10 native Ubuntu
in WSLg (WSL2)? Or even Ubuntu in VirtualBox in Windows?

Again .. pure guesswork.  I have no experience in your topic.  I just search around.

Further clues read here ...

[https://forums.linuxmint.com/viewtopic.php?t=60151](https://forums.linuxmint.com/viewtopic.php?t=60151)

---

