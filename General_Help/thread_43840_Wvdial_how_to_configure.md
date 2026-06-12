---
title: "Wvdial: how to configure"
date: 2005-06-23
forum: General Help
---

### Post by the_pc_dude on 2005-06-23
How do I Configure Wvdial

---

### Post by mad_alfred on 2005-06-23
[QUOTE=the_pc_dude]How do I Configure Wvdial[/QUOTE]
 just insert phone number, username and password in the wvdial.conf file ( just look for it with the find files utility...i'm not using ubuntu atm so i don't know where the file is actually stored)

to edit the file use:

sudo gedit wvdial.conf

now save the file and exit.

If when u connect using the wvdial command from root console u receive a message that tells you that the number/username/password are incorrect or invalid then edit again the wvdial.conf file and delete the ";" just at the beginning of the strings that contain the ph number, the username and the password. ( remember to delete alcso the space after the ";" ...it worked for me!)

cheers,
chris

---

### Post by the_pc_dude on 2005-06-23
thank you big time

---

