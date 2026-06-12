---
title: "Touchpad on Asus 1005HA"
date: 2014-04-06
forum: General Help
---

### Post by bluedingo on 2014-04-06
Just installed 13.10, touchpad not working. Made sure the Fn key didnt have it disabled and still nothing.

Here is xinput list

```
[COLOR=#000000][FONT=Calibri]asus@EeePC:~$ xinput list[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]&#9121; Virtual core pointer                        id=2    [master pointer  (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]&#9123; Virtual core keyboard                       id=3    [master keyboard (2)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Power Button                                id=6    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Video Bus                                   id=7    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Power Button                                id=8    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Sleep Button                                id=9    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; Eee PC WMI hotkeys                          id=12    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)][/FONT][/COLOR]
```

and lsmod

```
[COLOR=#000000][FONT=Calibri]asus@EeePC:~$ lsmod[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]nls_iso8859_1          12617  1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]vesafb                 13500  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]coretemp               13195  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]parport_pc             31981  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ppdev                  17391  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]eeepc_wmi              12983  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]asus_wmi               23495  1 eeepc_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]sparse_keymap          13708  1 asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]rfcomm                 53664  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_hda_codec_realtek    50315  1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]bnep                   18959  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]bluetooth             323656  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_hda_intel          42658  3 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_hwdep              13272  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_pcm                89488  2 snd_hda_codec,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_page_alloc         14230  2 snd_pcm,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_seq_midi           13132  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_seq_midi_event     14475  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_rawmidi            25094  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]uvcvideo               71309  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]videobuf2_vmalloc      13048  1 uvcvideo[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]videobuf2_memops       13170  1 videobuf2_vmalloc[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]videobuf2_core         39125  1 uvcvideo[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]microcode              18894  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]videodev              107508  2 uvcvideo,videobuf2_core[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]arc4                   12536  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ath9k                 136361  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]serio_raw              13189  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]lpc_ich                16864  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]i915                  594442  3 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ath9k_common           13619  1 ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ath9k_hw              429197  2 ath9k_common,ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ath                    19187  3 ath9k_common,ath9k,ath9k_hw[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]mac80211              517444  1 ath9k[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]cfg80211              401762  3 ath,ath9k,mac80211[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]drm_kms_helper         46867  1 i915[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd_timer              24447  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]drm                   242400  4 i915,drm_kms_helper[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]soundcore              12600  1 snd[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]i2c_algo_bit           13197  1 i915[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]video                  18777  2 i915,asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]wmi                    18590  1 asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]mac_hid                13037  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]lp                     13299  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]parport                40795  3 lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]hid_generic            12492  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]usbhid                 47361  0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]hid                    87370  2 hid_generic,usbhid[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]usb_storage            48294  1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]ahci                   25579  2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]libahci                26619  1 ahci[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]atl1c                  40949  0 [/FONT][/COLOR]
```

Touchpad is enabled through dconf and I tried 
sudo modprobe -rv psmouse 
sudo modprobe -v psmouse

Still nothing. Help would be very appreciated.

---

### Post by Jason_Minns on 2014-04-06
[http://www.uplawski.eu/technology/linux/touchpad_en.html](http://www.uplawski.eu/technology/linux/touchpad_en.html)
Try this. It just had this happen to me. I belive this is what I had to do or something real similar. 
Good Luck.

---

### Post by bluedingo on 2014-04-06
My touchpad though doesnt appear in xinput list, only Virtual core XTEST pointer. So now what?

---

### Post by Jason_Minns on 2014-04-07
I reposted this question in Linux Forums to see if anyone over there knows. I'm curious myself as to a solution. Hopefully we can figure it out.

---

### Post by Jason_Minns on 2014-04-07
This was one reply from a member at Linux Forums:

It looks like you've dug fairly deep. I haven't played with it yet. I'm  *assuming* it comes with unity as the default DE and that's what you're  using?
 
They keep taking stuff out of the main line DE. Does it still have a  control panel and if so does it have mouse/touchpad settings. You may  need to play with those.
 
If they've taken it out of unity then you might want to install the  gnome DE. It will give you access to a lot more tools. Or install one of  the modules that let you access those settings.
 
You might also need to install drivers or other support libraries. If  you search the repos for "synaptic" there's all kinds of stuff;  including xorg touchpad drivers.
 
It might need a kernel update? Or a specific kernel?
 Here's one reply:

It might need a linux firmware update? Or to change the firmware version to include non-free firmware?
 
You might also need to enable "universe" / non-free(?) / backports in your repo manager.
 
Or it could be an issue with power settings; either in BIOS or boot  options or configuration within the OS. And not just touchpad hardware  specific power options either. Take a look at your ACPI and xset  settings.
 
And installing juipter from webupd8 may help. But that one is at your own risk. Research it first.
 
If none of that works you might want to put 14 on it. The release is  scheduled for this month. Since it's a LTS they are usually easier to  work with and have better hardware support than the shorter lived point  releases.

---

