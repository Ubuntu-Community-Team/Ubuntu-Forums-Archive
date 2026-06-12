---
title: "ubuntu 13.04 run python script when deviced is plugged in"
date: 2013-06-23
forum: General Help
---

### Post by AgentZ86 on 2013-06-23
Hi
How to autorun a python script when media player is plugged in ?

I created the file ~/.local/share/applications.usb-copy.sh
This is the main one that will run when a device is inserted
[http://bpaste.net/show/VPz9P4uxn4eSzv5mXO3l/](http://bpaste.net/show/VPz9P4uxn4eSzv5mXO3l/)
I also added it to the .local/share/applications.usb_devices.desktop with the following lines added
> [Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=gnome-panel-launcher
Name=usb_devices
Exec=/home/agent86/Documents/usb-copy.sh %U
Comment=usb copy script

And my python script is:
[http://bpaste.net/show/baQ0mcuxoqJAyG7Lj9Do/](http://bpaste.net/show/baQ0mcuxoqJAyG7Lj9Do/)

I then selected System Settings / Details / Removable Media / Music Player / Other Applications from the pulldown menu
Then selected usb-copy from the menu.
So now when the device is plugged in the usb-copy.sh script runs which refers to my python script as well.
The line items for the script run and the notification parts run fine.
However, when it gets to the line item for the python the script, the python part does not run.

I can type it manually in the consol such as:
bash usb-copy.sh and the python part runs perfectly

So why doesn't the python part run when the device detection runs the script ? Why is this any different then running in the console  ?

Please advise

---

### Post by AgentZ86 on 2013-06-27
Solved my own thread

Still have to create a .desktop items in this case for me I created
> [Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=gnome-panel-launcher
Name=usb_devices
Exec=/home/agent86/Documents/usb_devices/usb_devices.py %U
Comment=usb copy script

Now I can select usb_devices from the applications menus
Or with System Settings / Details / Removable Media / Music Player / Other Applications from the pulldown menu to select my **usb_devices** application

I had some problems with the working directory of the script not being able to access the .wav files I referenced.
So that was my problem. Python silently failed and did not give me any indication since the consol did not run during the device plugin but simply processed and could not find the .wav file
After some adjustments to the path such as:
> dirpath = os.path.dirname(os.path.realpath(__file__))

My python script starts, detects media player, copies files and exits peacefully

---

