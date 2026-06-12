---
title: "wow lags"
date: 2007-10-18
forum: General Help
---

### Post by 99bluefoxx on 2007-10-18
hi
i got world of warcraft working on my comp but its got a relatively low framereate
if i start it up and im in an inn, it will say 1000fps, lag then drop to as low as 6 fps
average is around 8-14, depending on area, population and those types of factors
i am attatching two logs from running it in terminal for around an hour and no crashes, as well as my wtf config file
i am also using some UI addons[FUbar] and my wine version is wine-0.9.47
i also have used the mods from [http://ubuntuforums.org/showthread.php?t=303509](http://ubuntuforums.org/showthread.php?t=303509) , to no avail
any help would be great
Edit: i am adding my hardware info, in case that will help
mobo:asrock p4vm890 intel via chipset, defualt bios
ram: mis-matched 1.5gb ttl 1gbpc3200 w/th heatspreader and 512mbpc3100, flexability enabled
HDD:seagate ultra ide pata 250GB
vid card:PCI 256 bfg graphics nvidia 6200 oc
dual cd rws, one dvd rom[2 cd drive ttl]
mmc card reader, with usb
300W psu
logitech lx700/lx7 kbd/mouse set, cordless
acer al1716 lcd moniter
celeron D 2.93ghz socket 478 processor, overclocked to around 3.54 ghz[is still stable]
random working sound card[cmi8738 model 5 according to hwdinfo]
3c905 100baseTX boomerang 3com network adaptor card


edit2:i patched this morning and it wouldnt work at first, after fiddling with config.wtf again i got it working but now launch-wow.sh isnt working, but i think thats my terminal cause that seems to have died altoether

---

### Post by 99bluefoxx on 2007-10-18
anything at all?

---

### Post by antoniuk on 2007-10-19
You have a Celeron CPU, mismatched ram down clocked to pc 2100, A PCI video card and you are emulating a Windows game through Wine with little or no optimization and no native direct x support at all.

It is going to be all kinds of laggy, in fact it would lag on a windows PC.

You would be lucky to get 20 FPS at 800x600 in a low framerate area. What you get is about right for your system and running it through wine

On top of it all you are overclocking your CPU something crazy and I bet you don't have anything but stock cooling.

While that 300 Watt PSU will run your computer, be careful you don't undervolt the system and fry the hardrive or worse.

---

### Post by 99bluefoxx on 2007-11-13
i actually have upgraded the cpu fan on my comp as the origanal was crap, and just installed an extra gig of ram so im running 1.5 gb now
however last night wine was updated and while thats fine, wow is dead alltogether, after patching this morning it does nothing at all
the launch shell script is non working, it launches then the terminal window dissapears. the cpu overclocking isnt as bad as ive seen done[a buddy of mine oced his processor 2 ghz with an external fan]
adding the ram seemed to help and theyr both pci 3200 now, it also has a heatspreader, so that also helps. i was actually getting upto 50 fps in instances the past week after adding the ram, then it patched and died. i really cant reinstall from scratch again, as i only have a 30 kb/ps net connection and can afford anything better or else i  would upgrade it
any idea beyond that?

---

