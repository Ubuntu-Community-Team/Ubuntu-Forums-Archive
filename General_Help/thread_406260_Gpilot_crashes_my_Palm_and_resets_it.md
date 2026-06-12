---
title: "Gpilot crashes my Palm and resets it"
date: 2007-04-10
forum: General Help
---

### Post by wulfhound on 2007-04-10
I've had it working with Jpilot in Xubuntu. I am now running Ubuntu.

I run Ubuntu from the command line, and this is what I get:

"finn@crapadoodle:~$ gpilotd
gpilotd-Message: gnome-pilot 2.0.14 starting...
gpilotd-Message: compiled for pilot-link version 0.12.1
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] 
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 0
gpilotd-Message: Watching Palmpilot (/dev/pilot)
gpilotd-Message: Found 4766, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0502, 0736
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 091e, 0004
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 115e, f100
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0100
gpilotd-Message: Using net FALSE
gpilotd-Message: Found 082d, 0200
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0300
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0c88, 0021
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0002
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0003
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0020
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0031
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0040
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0050
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0060
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0061
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0070
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0080
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 8001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 6601
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0038
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0066
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0095
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 009a
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00c9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00da
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00e9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0144
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0169
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 12ef, 0100
gpilotd-Message: Using net TRUE
gpilotd-Message: setting PILOTRATE=9600

(gnome-pilot:11715): gpilotd-WARNING **: pi_accept_to returned -202: No such file or directory

(gnome-pilot:11715): gpilotd-WARNING **: pi_accept_to: timeout was 2 secs"

I tried to run the gui and I set it to get the user id and device number from the Palm, it freezes the program.

Sandaili

---

### Post by bedohave on 2007-04-17
Hi sandaili,

It may be that the directory/folder gpilotd is looking for doesn't exist.

Try this:
[LIST=1]
[*](left) click on the gnome-pilot applet icon
[*]select your PDA (likely it's the only one listed)
[*]Click on the "Edit..." button
[*]What is the name folder in the "Local folder:" field?  This is the place that gpilot uses to keep sync history and backups of your data. If none exists, enter one.  For example, I use /home/*myusername*/MyPDA  (replace, of course,  '*myusername*' with your username)
[*]Confirm that that folder/directory exists.  If not, create it (paying attention since file and directory names are case-sensitive)
[/LIST]

Or, you may have more luck by trying different device settings.  For example, under Edgy, I used /dev/ttyUSB2.  Under Feisty, I'm using usb:

Restart gpilotd and the gnome-pilot applet (or reboot, an effective if brutish approach).

All the best

---

### Post by defishguy on 2007-07-18
My palm does not synch when I try to add the "To Do" conduit.  Try selectively removing the conduits your syncing with until it actually syncs.

Good luck!

---

