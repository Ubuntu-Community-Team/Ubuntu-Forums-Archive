---
title: "Sound Skipping in VMWare with Windows 98 Guest Os"
date: 2007-05-01
forum: General Help
---

### Post by BriLarks on 2007-05-01
When I loaded my copy of Windows 98 onto a virtual machine the sound was terrible. It skipped really badly.:(  I searched the web and found nothing of use. I also looked at VMware's official howto and found some of it's advice to be misleading. This is a summary of VMware's advice:

[http://www.vmware.com/support/gsx25/doc/vidsound_sound_gsx.html](http://www.vmware.com/support/gsx25/doc/vidsound_sound_gsx.html)

[LIST]In your .vmx config file add the following two variables "sound.maxLength and sound.smallBlockSize"
[/LIST]

[LIST]These parameters should be set to powers of two i.e. 64,128 or 512
[/LIST]

[LIST]To Stop the skipping set the values to lower than 512
[/LIST]

[LIST]maxLength has to be greater than or equal to smallBlockSize
[/LIST]

The third of these points is the one I found to be misleading. :confused:  I tried almost every combination in the range 2 to 512 (46 times I shut down my virtual machine changed the settings and started it up again). None of the combinations in that range improved the sound quality. Finally I became adventerous and set the maxLength to be above 512. I finally settled on a maxLength of 8224 and a  smallBockSize of 512. This combination totally removed the skipping from my setup. It seems that it is the maxLength that is the important variable so change that one first. 

I hope my blind experimentation saves someone else the trouble. Although I don't imagine too many people are trying to run Windows98 in a virtual machine from Ubuntu!:lolflag:

When I'd finished my sound settings looked like this.

# Sound settings
sound.present = "TRUE"
sound.virtualdev = "sb16"
sound.synth.operational = "TRUE"
sound.maxLength = "8224"
sound.smallBlockSize = "512"

---

