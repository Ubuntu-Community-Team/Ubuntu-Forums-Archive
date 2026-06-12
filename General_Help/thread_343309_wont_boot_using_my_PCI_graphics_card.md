---
title: "wont boot using my PCI graphics card"
date: 2007-01-21
forum: General Help
---

### Post by Mmmbopdowedop on 2007-01-21
OK . . . 

i installed the latest Ubuntu CD 6.10 Edgey and wen i try and boot it wont.

it gets to the laoding screen and then stopped, i changed my graphics options in my bios to use the onboard instead of my PCI card and it worked OK, booted great.

Is there an easy way (as im a beginner) to change it so that when ubuntu laods, it uses my onboard to boot and then changes to use PCI as a secondary but by using only 1 monitor, making it so that i cannot see the boot screem as  im not too fussed about, or if theres a simple way to just sort it  :confused: 

My PCI Graphics Card Is ATI RADEON 9250

thanx

---

### Post by Ramses de Norre on 2007-01-21
Boot from the onboard and edit /etc/X11/xorg.conf, search the device section for your video card and change the driver to vesa (only the video driver!), so the driver line should look like this:```
        Driver          "vesa"
```
Then try to boot with your ati card. If that works you can install xorg-driver-fglrx, change the file again and set the driver to fglrx and restart X.

---

### Post by Mmmbopdowedop on 2007-01-21
i think i did what you said, but it didnt work, it still froze half way through the boot menu,

here is what i changed in my xorg.conf

i only changed teh driver like you said, hope it was the right bit.

> Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

any other ideas, thanx for replyin aswell ;)

---

### Post by Ramses de Norre on 2007-01-21
At exactly which sequence does it freeze during boot?
You can see that if you press 'e' in grub, go to your kernel line and press 'e' again, then remove the word 'quiet', press 'enter' and then 'b'.

---

### Post by Mmmbopdowedop on 2007-01-21
sorry, im hopeless :s

i rebooted several times and pressed 'e' quite a bit during boot and nothing happened :s 

no screen comes up or anything

grub starts on its own automatically, i dont get any choices or anything :confused:

sorry . . . . found it ...... just try it now ;)

did a serch, didnt see ya need press 'esc' ;)

---

### Post by Mmmbopdowedop on 2007-01-21
OK . . . . . 

i did what you told me once again and here are the last few lines that i saw before it froze . . 

> [COLOR="Blue"]

running /scripts/local-top                 ok
running /scripts/local-premount                 ok
running /scripts/local-bottom                 ok
running /scripts/init-bottom. . .
reading files needed to boot . . .
setting preliminary keymap . . .
starting basic networking . . .
starting kernel event manager . . .

[/COLOR]

[COLOR="Red"]and thats where it froze[/COLOR] :(

---

### Post by Mmmbopdowedop on 2007-01-21
[COLOR="Blue"]
i dont think its a problem with ubuntu, as i tried SuSE and the same problem occured there

also i tried the GParted Live CD and that didnt work neither

so it muct be something with the kernel or something technical like that lol

thanx for ya help eniways[/COLOR]

---

### Post by po0f on 2007-01-21
Pey Tudor,

Don't give up, an answer is only a [click](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) away.

[EDIT]

The link is titled ambiguously, it should work in your situation (ATi card) as well.

---

### Post by Mmmbopdowedop on 2007-01-22
Thanks alot for that po0f,

when i went into the xorg.conf file, is there ment to be both graphics cards in there???

because i only see my intel 1 :(

i tried it anyway, and still nothing happens, freeses at the same point, tried booting in recovery mode and just as it froze it threw loadsa stuff up about the intel agpgart thingy, so i dont think it disables it like it should have done :( thanx for helping though ;)

---

