---
title: "No sound whatsoever, all hdmi unplugged"
date: 2016-12-13
forum: General Help
---

### Post by abhishek_singh2 on 2016-12-13
I have no sound whatsoever. I'm running 16.04 on kernel version 4.4.0-51-generic. I have Pulseaudio which shows all HDMI outputs as unplugged.

alsamixer shows two cards HDA Nvidia and HDA Intel. The default one is Intel and none of the cards are muted.

> aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> lspci | grep -i audio

```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

---

### Post by mastablasta on 2016-12-13
similar issue - sometimes i can solve it by:

```
sudo alsa reload -c
```

this reloads the modules. 

another option is this: 
```
[FONT=Courier New]pulseaudio -k && sudo alsa force-reload[/FONT]
```

But sometimes these sort of reloads are not enough and i have to turn it off (unplug the power) for 20 sec. then reboot and run the alsa reload.

i am curious - is nVidia actually a sound card or just a chip on motherboard?

Also run this command and check for errors in output (cou can also see dmesg in system log viewer of your choice):

```
dmesg
```

---

### Post by abhishek_singh2 on 2016-12-13
Okay, the reloading thing didn't work. Despite reloading, some modules didn't unload.

```
[COLOR=#333333]Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).[/COLOR]
[COLOR=#333333]Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer.[/COLOR]

```

I have no idea about the Nvidia card. I have a Nvidia GPU, the Geforce 310 running on 340.98 drivers.

I couldn't really see any dmesg errors. It ran fine. Here's the output if you want it [http://pastebin.com/KPPYQEWC](http://pastebin.com/KPPYQEWC).

It does show that Nvidia is somehow tainting the kernel and [COLOR=#333333][FONT=Consolas]VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround. Also, [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000000000000800-0x000000000000084F (\PMRG) (20150930/utaddress-254).[/FONT][/COLOR]

Anything else that can help? Thank you.

---

### Post by abhishek_singh2 on 2016-12-13
Here's alsamixer for both cards btw.

[IMG]https://s23.postimg.org/q2gt7dli3/Terminal_abhishek_ubuntu_001.png[/IMG]ds.[IMG]https://s23.postimg.org/qgi56z5ln/Terminal_abhishek_ubuntu_002.png[/IMG]

---

### Post by mastablasta on 2016-12-15
ok so nVidia is then mentioned as there is porbably a HDMi output (which includes sound) on the graphics card.

it does similar thing to me sometimes as well (doesn't unload all the modules). try turning it off, tkaing away all power and then bootign the machine and run the command. sometimes i need to run it two times for it to work. if it doens't unload all the modules then it looks like something is "stuck". i am not sure i understand how this happens or Works, but that's what it look like in my case.

the "tainting kernel" is probably the GPU drivers patching the kernel. this is not an issue here.

is there any line about audio in dmesg? sorry for all the questions, but pastebin is blocked where i work :-)

or about sound. it might says HDA intel or something like that.

occasionally i would get "spurious response" messages for the intel chip.

---

