---
title: "Someone care to explain what all this is?"
date: 2007-04-03
forum: General Help
---

### Post by pappy on 2007-04-03
Hi all i tried to run Kate from a terminal and i got this message

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
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-4891' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kate: WARNING: Pixmap not found for mimetype application/vnd.oasis.opendocument.presentation
kate: WARNING: Pixmap not found for mimetype application/vnd.oasis.opendocument.presentation
kate: WARNING: Pixmap not found for mimetype application/vnd.oasis.opendocument.presentation
kate: WARNING: Pixmap not found for mimetype application/vnd.oasis.opendocument.presentation
QFile::open: No file name specified

Something like that i get when i try to run beryl-manager. But in the case of beryl the screen goes black and freezes and i have to restart X. I read in a post that responsible are these lines in the xorg.conf file in the sections 
Section "InputDevice"

Identifier "stylus"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY

And also these in the ServerLayout section

InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents
When i put the # i lost the windows basically and i had to edit the xorg.conf file from the command line and now i'm OK.
Doea\s anyone have any idea what these are and how (and if) they are connected with beryl not running.
Thank you for your help

---

