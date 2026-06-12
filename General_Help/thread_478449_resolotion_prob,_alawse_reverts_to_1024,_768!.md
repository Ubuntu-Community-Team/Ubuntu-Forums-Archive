---
title: "resolotion prob, alawse reverts to 1024, 768!"
date: 2007-06-19
forum: General Help
---

### Post by hessiess on 2007-06-19
nivida dirver works perfect exept for this little problem. i haft to fix the widescreen resolotion every time i reboot the comp, laptop so this is dun regually! when i try to save a xconfig file from the driver screen it outputs tuns of errors, carnt rember what thay are now. post them latar;)
any ideas?

---

### Post by longlegs on 2007-06-21
Hi,
It sounds like you need to edit the /etc/X11/xorg.conf file. For instructions see my earlier post. ie search for 'Low Resolution Problem', Read also the reply by phr0ze in same thread.
Good luck
longlegs

---

### Post by SendDerek on 2007-06-21
Have you checked the "Make this the default settings for this machine" check box under the Resolution Preferences?  

This helped me out because my refresh rate was always wrong on startup.

---

### Post by hessiess on 2007-06-22
im setting it using sudo nvidia-settings. on the set desktop res 1024 is the max for some resin

---

