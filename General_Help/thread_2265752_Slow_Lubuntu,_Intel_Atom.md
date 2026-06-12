---
title: "Slow Lubuntu, Intel Atom"
date: 2015-02-17
forum: General Help
---

### Post by richardjwentworth on 2015-02-17
[FONT=arial][SIZE=3]Hello all. I have recently switched from Windows 7 starter to Ubuntu. After playing with that for a bit and still finding it to be slow I switched to Lubuntu. Still It is a bit slow (Nothing compaired to windows though). Now I am VERY new to linux so I am not sure where to begin to find the trouble with speed on my system. I am using lubuntu on an Acer Aspire One that has an Intel Atom cpu (1.66GHz), 1GB. While I know I will never be able to game on this system I figured I would be able to at least browse the internet and watch streaming videos without skipping, stuttering, and freezing.[/SIZE][/FONT] [FONT=arial][/FONT][FONT=arial][SIZE=3][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]I find that even just scrolling down a page in firefox/crome is not smooth. Looking at my task manager I see that only 345 of 991 MB used as far as ran but my cpu is all over the place ecpecially after switching windows (The more is switch the higher it goes) I would prefer to use ubuntu over lubuntu as I prefer the look of ubuntu but not the performance on the netbook. Any help on how to get started figuring out why this thing is running slow would be helpful and very much appreciated.

P.S. I am not sure why but every time I boot up the system I get a message saying system error detected and asks me to report it but it doesn't say what the error is. I don't know if that is relevant to the slowness or not.

Again thank you for any help offered.
Rick
[/COLOR][/SIZE][/FONT]

---

### Post by kerry_s on 2015-02-17
sudo apt-get install intel-microcode   <--firmware updates for intel cpu
sudp apt-get install linux-image-generic-lts-utopic  <-- 3.16 kernel runs much better

reboot for those to take effect

in you bios, change video to "dvtm" & "maximum dvtm"  that will give you all your ram, it will give video ram when needed on the fly.

i'm not sure what the editor in lubuntu is, so i'm going to use "leafpad" as a example, cause it's the most likely choice for lite editor.

press alt+f2 to get the run dialog or in terminal.

gksudo leafpad /etc/X11/xorg.conf

copy & paste this:

Section "Device"
	Identifier "Intel Graphics"
	Driver "intel"
	Option "AccelMethod" "uxa"
EndSection

---

### Post by richardjwentworth on 2015-02-17
Thanks I will try now!

---

### Post by richardjwentworth on 2015-02-17
Ok so I tried the fixes you posted. On the second command I assumed sudp was a typo so I used sudo. The second command gives me the error "E: Unable to locate package linux-image-generic-lts-utopic" and my bios does not have those settings unfortunatly. Using the other things posted did not seem to help much. :(

I would actually say that it seems to be running slightly worse than before. Maybe because I wasn't able to do everything listed?

---

### Post by kerry_s on 2015-02-17
yeah typo, fat fingered it. lol
bummer, those settings really help save ram from being taken by vid when not needed.

not sure about the kernel error. i'm sure i got the name right. see pic

---

### Post by richardjwentworth on 2015-02-17
Thanks for the help Kerry. After searching around a bit more I found a guid for speeding up ubuntu and it seemed to help a bit. Still not as snappy as my desktop machine but I probably shouldn't expect it to me. I think my next step should be to upgrade the ram (Can only upgrade to 2GB) and possibly a ssd to help speed a bit. Again thank you so much for your advice!

---

### Post by kerry_s on 2015-02-17
yeah, thats what i did. maxed out my ram to the 2gb & i grabbed a 60gb ssd when they were on sale during xmas.

---

