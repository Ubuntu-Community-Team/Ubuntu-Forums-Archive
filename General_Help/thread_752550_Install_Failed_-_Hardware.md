---
title: "Install Failed - Hardware?"
date: 2008-04-11
forum: General Help
---

### Post by Gripp on 2008-04-11
i first tried installing it on my riad0 drive - didn't go so well... just took me to generic promt

then i tried in my back up drive (non raid) and it took me to boot up screen and began the install, got mostly through and then failed during the "configuring hardware" bit

it only told me that it saved a zip file to my drive - but the file seems to contain every log possible. 

my hardware is:

Intel Q6600 G0 (not OC'd)
ASUS maximus formula special edition MOBO
2x1GB crucial ballistix DDR2  pc6400
EVGA 8800 GTX800 
Corsiar 520WHX PSU
2x Seagate Barracuda 7200.10 250GB (perp recording) in raid 0 X256 stripe
1x Seagate Barracuda 7200.10 250GB (perp recording) 
SAMSUNG Black 1.44MB 3.5" Internal Floppy Drive
SAMSUNG DVD Burner SH-S203B 
SAMSUNG HLR5678WX (TV acting as monitor)
Logitech 
MX5000 bluetooth keyboard and mouse

my BIOS is flashed to almost the latest (the 9x series has issues from what i read) but all of the rest of my hardware is as up to date as can be.

something else to note as well, (not sure if it's relavent) the keyboard worked fine when i was dumped into the command prompt, but not at all (nor my nouse) when the install was actually trying to take

edit: i was installing with the 8.04 beta wubi

---

### Post by ago on 2008-04-12
please attach the zipped log file

---

### Post by Gripp on 2008-04-12
i went to upload the file and realized that it was deleted when i ran the uninstall for wubi...

so i tried to reinstall it to get the same error, but didn't
i got through the install, but this time after it rebooted itself it gave me this error:

booting 'ubuntu hardy (developement branch), kernel 2.6.24-16
filesystem type is fat, partition type 0xC
kernel /boot/vmlinux-2.6.24-16-generic root=/ubuntu/disks/root.disk
ro quiet splash
error 15: file not found

press any key to continue...


i guess i'm going to try one more time... maybe three's a charm?

edit:  i also notice that the file it saves to backup on uninstall is named "hardy-desktop-amd64.iso"
given that i have an intel this seems off...

---

### Post by ago on 2008-04-12
Are you sure it is root=/ubuntu/disks/root.disk and not loop=/ubuntu/disks/root.disk?

---

### Post by Gripp on 2008-04-12
(i wrote down "loop" but i may have been assuming)
third time was "half-way" a charm

i am typing now from ubuntu - however, it only got a small percentage through the install (maybe 5%) and said something about the disk image being dirty (um, its an iso?)
but when i hit okay, it booted me in rather than restarting the comp...!?

i've played around with a couple of progs and everything seems to run just fine so far.  am i asking for trouble?

but i do have a small prob now - it doesn't want to recognize my wireless board and mouse.  i had to go digging in my closet for some wired stuff

the board worked in the command prompt, and i'm sure if a search around i'll find something...

---

### Post by ago on 2008-04-12
You might be in a live environment which is read only (changes are lost when you reboot).

---

### Post by Gripp on 2008-04-12
yes. yes i was.

everything worked great - even got my mouse working
but when i restarted the machine it went back to trying to reinstall but wouldn't go anywhere becuase it said that it was already installed (then why not the option of booting into that install??) and that i had to uninstall that instal before continuing

so, maybe lucky try 4?

---

### Post by jcsaintpo on 2008-04-12
i noticed too that when i installed via wubi 8.04 beta!
i got a live session on my computer and not an installed version!

this besides that HAL is failing to initialize

---

### Post by Gripp on 2008-04-12
sorry about your HALD errors, i had that on the last machine that i tried to install linux on... and never got that resolved either

but okay, so now i'm ALWAYS getting the dirty image error.  i've tried with the 64 bit image and the 32... so i dont think it is the image
so i started running chkdsk on my disks and yeah i had a number of errrors on both of them

but, even after they have been fixed i am still getting the error...?

Edit:
i attached the wubi log file.  the last line says the install was sucessful... not true.  and it doesn't appear to say anything about the image not being copy-able.
i've been giving some thought to the idea that my drives are corrupt.. it makes no sense.  the first couple of tries didn't give me this error. 
unless... one of my tries stuck me in an endless prompt - press okay and it comes right back.  no amount of ctrl alt dlt etv. got me out of it so i hard booted... but chkdsk says 0 bad sectors...

soo confused, its late too. think i'll try again tomorrow

---

### Post by ago on 2008-04-13
The above log is fine, and it seems that the Windows part of the installation was completed.
Then of course there is the Linux side of things (after reboot)... Uninstall, reinstall using the latest version in [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

If you have problems there should be a message that talks about logs. Said logs will be in c:\ubuntu\installation-logs.zip. Post it here.

---

### Post by Gripp on 2008-04-13
I used the latest (879sh or something thereabouts) and it didn't give me that error
it gave me the first one, and yes, that was loop=/ubuntu/...
not root

but i went in and changed it from hd(2,0) to 1,0 and it came up just fine :)

i'm in linux :) :guitar:

got my mouse and keyboard connected too, but the keyboard disconnected itself halfway through me posting this.,.. i guess that is my next big thing to worry about :)

thanks!

---

