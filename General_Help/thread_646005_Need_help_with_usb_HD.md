---
title: "Need help with usb HD"
date: 2007-12-20
forum: General Help
---

### Post by Takuhari on 2007-12-20
i need to change the setting on my usb hd...
It says that it is set to read only...

i went to properties and tried to click the write box, and it says permission denied...

through the terminal, i went to media/
sudo chmod 666 LACIE 
(lacie=my hd)
and it said:

chmod: changing permissions of 'lacie/': Read-only file system

any suggestions?

---

### Post by ijason on 2007-12-20
which version of ubuntu are you running?

---

### Post by Takuhari on 2007-12-20
version 6.06 i think...

it useto work... but then i used it on a windowz machine... then it didnt work... damn windowz!!!

---

### Post by ijason on 2007-12-20
it's no problem. :)  you just need to load an extra driver to give ubuntu read/write abilities for the ntfs/fat32 drive. give me a moment to find the name of it. you just apt-get it and then mount the drive with the new driver and you should be good to go.

---

### Post by ijason on 2007-12-20
here we go :
> sudo apt-get install ntfs-3g ntfs-config

and then to mount ntfs drives you go :
> sudo mount -t ntfs-3g /dev/sda1 /media/mydrive
where "/dev/sda1" is the physical path to the drive
where "/media/mydrive" is the path to the mount-point directory

you'll then need to chown the drive AND the mount-point directory to yourself, and also chmod them both. it's a bit of a chore, but i think the chown and chmod part you only have to do once. good luck!

**this is assuming your drive is NFTS formatted?**

---

### Post by Takuhari on 2007-12-20
takuhari@CrazyTacoCafeteria:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

---

### Post by ijason on 2007-12-20
what the duce? are all your repositories enabled?

you might be able to find them in the synaptic package manager?

as far as i've found, the only way to get ubuntu older than 7.10 to have fully functioning read/write abilities for NTFS drives is to use the ntfs-3g driver to mount the device.

---

### Post by Takuhari on 2007-12-20
hmmm.... you just spoke &#54620;&#44544; to me^^*

I had someone setup my ubuntu^^*
... maybee its located somewhere else... like one file away...
i've had that problem before...

where would the origional file be located?

---

### Post by ijason on 2007-12-20
ha! ok, Synaptic is ubuntu's GUI driven application installer.. thing.

from the start menu go to : System > Admin > Synaptic Package Manager. 

it will pop up a window you can put phrases into to search for. i did a search for ntfs-3g and it does look like it's in there. you'll click the little box and choose to install the package. then you click apply and it fetches it and sets up the app :)

---

### Post by Takuhari on 2007-12-20
the only ntfs files i can find are...
S40umountfs and unmountfs...

one moment... let me try^^*

---

### Post by ijason on 2007-12-20
i don't think all your repositories are activated. 

open synaptic again, and look in the Settings menu, go to the repository option and make sure that ALL the boxes are checked in the "Ubuntu Software" tab. then try searching again.

---

### Post by Takuhari on 2007-12-20
not in the search...
i typed ntfs-3g in the synaptic pm

---

### Post by ijason on 2007-12-20
are all your repositories enabled?

---

### Post by Takuhari on 2007-12-20
yup.... all boxed are enabled

if it helps....

Thank you for your interest in Ubuntu 6.06 LTS
                - the Dapper Drake - released in June 2006.
i looked it up in my about ubuntu...


I really appreciate your help...
I will be gone for a few hours... so if i dont see you... i would just like to thank you for your time...

and have a marry x-mas^^

---

### Post by ijason on 2007-12-20
hmmm. boy, i don't know why you can't see the driver :confused:

it shows up in my synaptic. try going to their website : [www.ntfs-3g.org](www.ntfs-3g.org) , maybe your version of ubuntu is incompatible? i'm sure there must be a way to get the drive to work, but it looks like i may not know it!

---

### Post by ijason on 2007-12-20
good luck! :)

---

### Post by Takuhari on 2007-12-20
thanx:popcorn:

i'll figure something out

---

