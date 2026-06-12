---
title: "Help with hotkeys"
date: 2007-06-12
forum: General Help
---

### Post by Master Jedi on 2007-06-12
(kubuntu) I'm trying to set up some simple hotkeys to map the media buttons on my (Sony Vaio VGN-TX750P) keyboard to various funcions.

For instance:
- If Xine is active and I press Play/Pause, send it a Spacebar keypress

In the KDE Control Center -> Regional & Accessibility -> Input Actions console I added a new group "Xine" and to that I added a new Acion "Play/Pause". The action type is Keyboard Shortcut -> Keyboard Input. In the shortcut tab I pressed the "XF86PAudioPause" button. But no matter what I put in the keyboard input section, nothing happens when I press that key.

It does work, however, if I use key combinations that don't include the media buttons.

Additionally, using the media keys in Keyboard Shortcuts does not work either.

Is there anything out there that will work with these keys. The application recognizes that the keys are being pressed when setting the key mapping but does not respond to the keystroke otherwise.

---

### Post by DagMan on 2007-06-12
Maybe see if the keys have any bindings to the scripts in /etc/acpi for example

sudo /etc/acpi/mediabtn.sh
sudo /etc/acpi/mutebtn.sh
sudo /etc/acpi/playbtn.sh
sudo /etc/acpi/nextbtn.sh
sudo /etc/acpi/stopbtn.sh

and if those scripts do anything, change them to function on xine.

---

### Post by Master Jedi on 2007-06-13
All the scripts look something like this:
#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_PLAYPAUSE


I tried adding a command to the end of the script but it doesn't seem as though the command executes when the button is pressed.

---

### Post by Master Jedi on 2007-06-13
Using kHotkeys I can map the XF86Eject button to the "eject" command and it works, but it doesn't seem that I can map any of the other "XF86*" keys (the pause, stop, previous, and next keys).

---

### Post by DagMan on 2007-06-13
try looking at the generic files already existing in /etc/acpi/events
then open a terminal and enter
tail -f /var/log/acpid | grep "received event"
and see if when you use your keys you get any output when using the fn key combos.  If you get output you can either put it into the relevant file there in /etc/acpi/events to call on the appropriate script, or you can make a new file.  You can also make a new script in /etc/acpi that does something specific and hook to it through a file in /etc/acpi/events

If you don't get any output from the tail command then obviously this wouldn't work but don't give up on it as I've seen another way of finding events posted here and I don't remember what it was since I didn't have to use it.

---

### Post by Master Jedi on 2007-06-25
The play/pause, stop, media next, and media back don't seem to be logged.


However, the hibernate, AV mode, eject, wireless mode, LCD/external display, and magnifying glass (no idea what it did in windows, never used it) buttons all do.

Some of the buttons: wireless mode, LCD/VGA, and magnifying glass produce 2 messages

Wireless mode:
[Mon Jun 25 09:15:09 2007] received event "sony/hotkey SPIC 00000001 0000000c"
[Mon Jun 25 09:15:09 2007] received event "sony/hotkey SPIC 00000001 0000003b"

LCD/VGA:
[Mon Jun 25 09:15:41 2007] received event "sony/hotkey SPIC 00000001 00000012"
[Mon Jun 25 09:15:41 2007] received event "sony/hotkey SPIC 00000001 0000003b"

Magnifying Glass:
[Mon Jun 25 09:16:03 2007] received event "sony/hotkey SPIC 00000001 00000015"
[Mon Jun 25 09:16:03 2007] received event "sony/hotkey SPIC 00000001 0000003b"

---

