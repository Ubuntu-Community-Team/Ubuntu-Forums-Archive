---
title: "TC1100 stylus"
date: 2008-07-04
forum: General Help
---

### Post by Aloush on 2008-07-04
ok so i have posted before now i am ok just the sylus i need working this part id where i am stuck

  Stylus

The stylus lets you use the TC1100 as a Wacom tablet. Recent Ubuntu and Debian distributions detect and enable the tablet out of the box. To make it usable as a pointer, there are some changes needed in the X configuration file.

First you will need to figure out the device file to which it is mapped. If the file /dev/input/wacom exists, this is the device file you are looking for. If it doesn't, type:

$ xxd /dev/ttyS0

in the terminal and then move the stylus over the screen. If cryptic numbers (a hex dump) start to appear, this means that you have found the device name - in this case /dev/ttyS0. If nothing happens, try other serial ports - /dev/ttyS4 and /dev/ttyS14 are good first tries. Sometimes, the xxd command may freeze the system. In that case, you have probably tried the right port.

Edit your X configuration file (usually /etc/X11/xorg.conf) and add these sections. There are chances that some entries for the tablet already exist - in this case, modify the existing entries. You need three almost identical sections that differ only by the "Type" option. Although the pen doesn't have an eraser, this device entry is needed by some applications, notably wacomcpl.

Section "InputDevice"
   Identifier "stylus"
   Driver     "wacom"
   Option     "Type"        "stylus"
   Option     "Device"      "/dev/input/wacom" # put the device name here as found above
   Option     "ForceDevice" "ISDV4" # This enables a special communication protocol
   Option     "Button2" 	"3" # This is the line you need for the stylus button to right click
EndSection
Section "InputDevice"
   Identifier "stylus"
   Driver     "wacom"
   Option     "Type"        "cursor"
   Option     "Device"      "/dev/input/wacom"
   Option     "ForceDevice" "ISDV4"
   Option     "Button2" 	"3"
EndSection
Section "InputDevice"
   Identifier "eraser"
   Driver     "wacom"
   Option     "Type"        "eraser"
   Option     "Device"      "/dev/input/wacom"
   Option     "ForceDevice" "ISDV4"
   Option     "Button2" 	"3"
EndSection

If you want the stylus to function as a mouse, you will additionally need to modify the "ServerLayout" section of the file. Add the following two lines to the end of that section:

   InputDevice "stylus" "SendCoreEvents"
   InputDevice "cursor" "SendCoreEvents"



if i send somebody my xorg.conf can they edit it for me i am not sure where to put those chucks of writing

Thanks

---

### Post by romana on 2008-08-11
Try the [TC1100 thread]("http://ubuntuforums.org/showthread.php?t=563736&highlight=tc1100"):) Also, [my howto]("http://timelady.com/blog/howtos-technical-guidestips/kubuntu-804-hp-tc1100-tablet-functions-howto/"), which pulls together much that is on the thread:)

---

