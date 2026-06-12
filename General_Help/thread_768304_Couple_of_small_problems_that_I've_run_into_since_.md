---
title: "Couple of small problems that I've run into since upgrading to 8.04"
date: 2008-04-26
forum: General Help
---

### Post by Trapper Dave on 2008-04-26
I'm wondering if anyone could help me with a couple of small problems that I've run into since upgrading to 8.04.

[LIST]
[*][COLOR="Silver"]I have two drives; one which contains all of my files and documents, and the other which is broken into two partitions; one for my Windows installation and the other for my Ubuntu one. Is there anyway that I could get Ubuntu to mount my files and document drive on boot? - COMPLETED[/COLOR] I'm also wondering that if this is possible is it also possible for it not to show an icon on my desktop.

[*]Can anyone tell me what the terminal command is to find where a file is located? I remember doing it to locate where Pidgin was so that I could get it to run on boot.

[*]I'm having some sound issues, my sound card will work initially on boot and then just stop working. This usually happens once I open a second application that might use it. The only solution that I can find is to reboot; but that's a bit of a pain.
[/LIST]

---

### Post by ryanhaigh on 2008-04-27
To disable showing the icon on the desktop open gconf-editor (press alt-f2 and enter gconf-editor) search for volumes (with both boxes ticked) one of the results returned will be volumes visible or something similar, simply uncheck it. Note that this will effect all partitions including usb and cd drives.

To find where a program is located use ```
locate programname
```, generally they are in /usr/bin so I use ```
locate programname | grep bin
```. 

Can't help with the third issue as I am not using hardy.

---

### Post by Trapper Dave on 2008-04-27
Thanks for your reply. I managed to fix it before hand by automounting to a folder that I created in the /mnt/ directory. That removed the desktop icon.

Also I used the "which" command in terminal which worked out well.

---

