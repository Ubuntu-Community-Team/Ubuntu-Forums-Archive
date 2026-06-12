---
title: "WHat does this error message mean?"
date: 2007-04-27
forum: General Help
---

### Post by mykrob on 2007-04-27
Hey, i use Yakuake and launch a lot off stuff by console. Running Kubuntu Feisty..

Anyway, i ran kid3 to edit some of my MP3 tags.. It works fine, but the output in the console puzzles me:

```

family@infected-green:~$ kid3
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
family@infected-green:~$


```

what does this mean?

Thanks,
-mky

---

### Post by dreadlord_chris on 2007-04-27
Those errors refer to the input devices that have been installed by default in your X configuration, but which your machine doesn't actually have installed. i.e. wacom stylus, cursor and eraser

You can safely ignore them.

---

### Post by Stephen Howard on 2007-04-28
Presumably you don't have a wacom stylus, so make the message go away forever by deleting the wacom sections from your xorg.conf file.

PS:  I've heard that the error will confuse some scripts, so better to fix it than ignore it.

---

### Post by Nythain on 2007-04-28
or more safely just comment them out so the entries look like this:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```

---

### Post by mykrob on 2007-04-28
thanks, guys.

---

