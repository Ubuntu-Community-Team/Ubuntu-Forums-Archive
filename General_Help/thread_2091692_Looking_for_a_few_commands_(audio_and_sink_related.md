---
title: "Looking for a few commands (audio and sink related)"
date: 2012-12-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-12-05
I am looking for a command to get the default audio sink and the command to set the default audio sink

the goal is to make a script to toggle the Nvidia HDMI sound and the analog audio and also toggle the display using disper (disper -s / disper -S) i can determiner the active screen based on the current default audio sink
```
#!/bin/sh
ink="$(cat ~/.pulse/*-default-sink)"
analog="alsa_output.pci-0000_00_14.2.analog-stereo"
hdmi="alsa_output.pci-0000_01_00.1.hdmi-stereo-extra3"
if [ -n "$1" ];then
   if [ "$1" = "analog" ];then
      ink="$hdmi"
   elif [ "$1" = "hdmi" ];then
      ink="$analog"
   fi
else
   if [ $(zenity --question --text "Are you sure you want to switch Display Screens?" --title "Confirm";echo $?) -eq 1 ];then
      exit
   fi
fi
if [ "$ink" = "$analog" ];then
   disper -S
   pacmd set-default-sink $hdmi
else
   disper -s
   pacmd set-default-sink $analog
fi
```

---

