---
title: "Bluetooth freezing video on 16.04 Ubuntu and Kubuntu"
date: 2016-06-03
forum: General Help
---

### Post by SR71BB on 2016-06-03
When I watch a video using my Bluetooth headset the video plays at about 1 frame every 10 seconds. Essentially it's frozen.

 It is not browser specific and happens on multiple website, youtube, amazon prime, etc. I have not tested video playback on a stand alone player as I had no videos downloaded. 

I tried the beta version of Kubuntu 16.04 after a dirty update from 15.10. No issues on 15.10 but issues with 16.04 beta. I assumed it was the beta and did a fresh install of 15.10. 

When 16.04 was officially released I initially did a dirty update and got the same Bluetooth issue as before. So I did a fresh install of kubuntu 16.04 and still got the bluetooth issue. So I decided to do a fresh install of Ubuntu 16.04 as I read that it could be an issue with the audio backend like gstreamer and the thread said Ubuntu & Kubuntu use different ones, but I have exactly the same issue on Ubuntu 16.04 as well.

This is not specific to my hardware either. I did exactly the same as above with my laptop and it experienced exactly the same problems. Laptop has an intel 7260 card supplying the bluetooth connection and my pc has an Intel 8260 card.

Anyone know if this is a known issue and if it's being worked on?

I have found this bug officially reported and listed from older versions of Ubuntu but they are listed are fixed and closed.

I'm back on 15.10 now until it's fixed. Thanks.

P.S. Forgot to mention, but was implied, the issue does not exist on 16.04 when I use a wired headset.

---

### Post by jeremy31 on 2016-06-03
I wonder if the default parameters for iwlwifi have changed.  Please post the result of ```
grep [[:alnum:]] /sys/module/iwlwifi/parameters/*
``` from 15.10 and I will compare with results from my 7260 in 16.04

---

### Post by SR71BB on 2016-06-03
From my 8260 card... Booting up laptop now to get the 7260 readout[FONT=monospace][COLOR=#B218B2]
[/COLOR][/FONT]
```
[FONT=monospace][COLOR=#B218B2]
/sys/module/iwlwifi/parameters/11n_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/amsdu_size_8K[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/antenna_coupling[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/bt_coex_active[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/d0i3_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/fw_monitor[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/fw_restart[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/lar_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/led_mode[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/nvm_file[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#000000]([/COLOR][COLOR=#FF5454]**null**[/COLOR][COLOR=#000000])[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/power_level[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/power_save[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/swcrypto[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/uapsd_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR]

```[/FONT]

From the 7260 in laptop

```

[FONT=monospace][COLOR=#B218B2]/sys/module/iwlwifi/parameters/11n_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/amsdu_size_8K[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/antenna_coupling[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/bt_coex_active[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/d0i3_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/fw_monitor[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/fw_restart[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/lar_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/led_mode[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/nvm_file[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#000000]([/COLOR][COLOR=#FF5454]**null**[/COLOR][COLOR=#000000])[/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/power_level[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/power_save[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**N**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/swcrypto[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**0**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#B218B2]/sys/module/iwlwifi/parameters/uapsd_disable[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#FF5454]**Y**[/COLOR]
[COLOR=#000000][/COLOR]
[/FONT] 
```

Sorry for posting again, but I forgot to mention something in the original post that may or may not be important.

It's not just videos that freeze. I get zero sound from the headset when I try to stream online radio stations. An audio only stream. This may or may not help to pin point the cause.

---

### Post by jeremy31 on 2016-06-03
The parameters haven't changed at all in 16.04 but I did find some source code changes between the 4.2 and 4.4 kernel that concern bluetooth coexistence.  I will merge your last 3 posts into one just to make the thread easier to follow

This is really something that needs a new bug report filed for in order for it to be fixed in 16.04.  It is considered a regression but I know that changes were made in newer kernels to bluetooth coexistence for Intel.  It looks like the newer code is available in backports-20160216 that was updated 6 May 2016, so we do have a possible answer to the issue

---

### Post by SR71BB on 2016-06-03
That's great. I thought it would take a lot longer and a lot more investigation to find a cause. Thank you for helping.

Concerning the bug reporting, is that something you want me to do or is it something you have already done?

Thank you.

Edit: I will do a dirty install of 16.04 now over my current 15.10 and makes sure all backports get installed and test if the issue still exists.

---

### Post by jeremy31 on 2016-06-03
You will have to do it but if I find the same issue on my dell with 16.04 and intel, I will be able to add myself to the affected by list which should confirm the bug report.

See [this](http://ubuntuforums.org/showthread.php?t=1011078) for a tutorial on bug reports.  I would file the bug against package linux as it is likely a kernel issue.  File the bug with 16.04 installed and you can say that it worked perfectly in 15.10.  Once the bug report is confirmed, you may be asked to use the latest kernel to see if that fixes the issue

---

### Post by SR71BB on 2016-06-03
Edit: Forgot to mention... I did the update to 16.04 and the problem is still there. The readout below is from the error log using the 16.04 4.4 kernel.

Thanks, the report has been filed. Link is here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1589008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1589008)

When going through the error log the apport generated I noticed this:

```

Jun 03 23:45:41 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:45:41 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:45:41 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:45:41 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:17 username-MSI org.debian.AptXapianIndex[755]: Failed to import 'No module named 'glib'', can not use dbus
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:21 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:47:54 username-MSI org.debian.AptXapianIndex[755]: Failed to import 'No module named 'glib'', can not use dbus
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:50 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:48:51 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:00 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:15 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI kernel: show_signal_msg: 27 callbacks suppressed
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:33 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:34 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:36 username-MSI acpid[798]: input device has been disconnected, fd 12
Jun 03 23:49:40 username-MSI colord-sane[4250]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:42 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:45 username-MSI pulseaudio[1435]: [pulseaudio] module-bluez5-device.c: Default profile not connected, selecting off profile
Jun 03 23:49:47 username-MSI pulseaudio[1435]: [pulseaudio] bluez5-util.c: Transport TryAcquire() failed for transport /org/bluez/hci0/dev_B8_AD_3E_0A_2D_4E/fd0 (Operation Not Authorized)
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )
Jun 03 23:49:47 username-MSI org.kde.KScreen[1291]: kscreen: Primary output changed from KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" ) to KScreen::Output(Id: 453 , Name: "DP-4" ) ( "DP-4" )

```

Is this showing an issue with bluetooth? And if so is it showing something that has an easy fix?

---

### Post by jeremy31 on 2016-06-03
Only 2 lines are bluetooth related ```
Jun 03 23:49:45 username-MSI pulseaudio[1435]: [pulseaudio] module-bluez5-device.c: Default profile not connected, selecting off profile
Jun 03 23:49:47 username-MSI pulseaudio[1435]: [pulseaudio] bluez5-util.c: Transport TryAcquire() failed for transport /org/bluez/hci0/dev_B8_AD_3E_0A_2D_4E/fd0 (Operation Not Authorized)
```
A lot of the others look to be graphics related

---

### Post by SR71BB on 2016-06-04
Thanks, those were the lines that caught my eye but I just copied the entire log before and after them.

The not authorised in the bluetooth read-out is very reminiscence of a bluetooth issue that I had with my pi 3 a few weeks ago. I solved that after a bit of tinkering with the config files. Would those two error lines signify an issue with the bluetooth manager config files then instead of source code changes in the kernel?

---

### Post by jeremy31 on 2016-06-04
Those errors indicate an issue with pulse audio and bluez5.  I was not able to duplicate your issues with videos

---

