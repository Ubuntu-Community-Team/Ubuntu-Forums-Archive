---
title: "help? how do i edit xorg.conf from commandline?"
date: 2007-04-24
forum: General Help
---

### Post by Huzudra on 2007-04-24
i sort of messed things up messing around a little and i need to fix my xorg.conf now, but i dont know how to edit it from commandline!  i thought that removing xserver-xorg-core would remove all the config and put it back to how it was, then just reinstall the nvidia driver but that didnt work!  this all happened when i changed it from nv to nvidia and restarted.  i just need to change that back i think...:confused: :( i cant even rememeber the command to enable the driver now, its been a heck of a day and i just want to fix this.

i can see the file in windows with explore2fs but i cannot make changes to it, pretty frustrating!

---

### Post by robrmd9 on 2007-04-24
Hey, just do something like:

```
sudo nano /etc/X11/xorg.conf
```

This will open it up in nano, which is a command-line text editor.

---

### Post by itsjustarumour on 2007-04-24
Try:

> sudo nano /etc/X11/xorg.conf

---

### Post by itsjustarumour on 2007-04-24
I'll second that then, lol!  ;-)

---

### Post by Huzudra on 2007-04-24
thanks to both of you, i'll try this once i've downloaded the new image and burned it to CD just incase i cant get it fixed, i'll just format/reinstall.  there was nothing on there that was special, i just booted to it to check email/browse/chat on gaim.

---

### Post by Huzudra on 2007-04-24
while i appreciate the help, it didnt work out, says the file is empty or doesnt exist when i try nano, but i can SEE it when in windows or booted to the cdrom and its there and not empty!!!  but i cant write to it from either so im just going to reinstall.  now heres a good one, how come im having install problems now!

i formatted the partition it was on to ext3 again but it says theres no root file system installed? or am i mistooken and it should be ext2? nevermind, i need to learn to read whats on my screen!  its just one of those days!

---

### Post by strabes on 2007-04-24
The terminal is case sensitive. Make sure the "X" in "X11" is capitalized. /etc/X11/xorg.conf

---

### Post by Huzudra on 2007-04-24
thats good to know!  i just reinstalled, reinstalled the nvidia-glx, enabled it, same problem again!  yargh this is getting on my nerves now!  i really dont like a 60hz refresh rate so i'd like to get this working!  


so i wrote down the backup, tried to do it, it cant stat the backup file, no directory found!?  is that case sensitive too?  i think i got it down right, it should go like...

cp /var/backups/xorg/xorg.cong.2007-04-24-22:22:15 /etc/X11/xorg.conf

correct?  it says it cant find the backup file im pointing at, but now that i know the X11 part is case sensitive i think i can edit the config back to having the driver disabled so atleast i can use it again.  but why am i having it break each time i enable the nvidia-glx driver?  i dont think i need the legacy driver just yet, its an fx5700. i am soo very confused here!  i'd never had the driver enabled under edgy, it wouldnt let me saying something about how i had to manually edit it, i never got around to it.

edit, backup didnt work because thats not a 1, its a 4!!!  i cant see straight today.  guys i swear im not usually this mr magoo about things.


really the root issue, besides my ineptitudes today, is that whenever i enable the nvidia-glx xserver tosses itself out the window with a short rope around its neck.  i think the error is no device found or no monitor found.

back onto linux, got it updated.  it looks like the nvidia-glx when enabled points to a pci device, where as this system has an agp card installed?  i'm pretty lost on this one, i dont know that much yet.  how do i fix this?  60hertz hertz my eyes.

heres the bit from the config

Section "Device"
	Identifier	"nVidia Corporation NV36.2 [GeForce FX 5700]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by Huzudra on 2007-04-25
any thoughts on the nvidia-glx issue?  or should i start a new thread about this topic?:confused:

---

### Post by strabes on 2007-04-25
Read my whole post.

When you're typing directories & commands in terminal you can hit tab twice to show you all of the items in the directory you're pointing at. You can also type it and hit tab & it will complete the name for you. This way you avoid typos and the like.

You'll have to use "sudo cp" instead of just "cp" to copy root files.

> cp /var/backups/xorg/xorg.cong.2007-04-24-22:22:15 /etc/X11/xorg.conf

In the first part of your command it should be "xorg.conf" not "xorg.cong." So, if the rest of your filename is correct, the command you should run will look like this: 

```
sudo cp /var/backups/xorg/xorg.conf.2007-04-24-22:22:15 /etc/X11/xorg.conf
```

---

### Post by Huzudra on 2007-04-26
ya, i got that figured out, fixed my oops, but im trying to figure out why when i enable the nvidia-glx xserver stops working and says no devices found, no screens found.  the card IS an Nvidia FX5700, ive had it in and out several times and i know what it is, its not that im installing/enabling the wrong driver...its something else that i dont fully understand.  thats what im trying to solve now!

yes, i know i have to sudo for anything root.  the cong was a typo here, additionaly i had written the time stamp down incorrectly.  it was 22:22:45, not the :15 i had jotted down!  whoops!

---

### Post by Huzudra on 2007-04-26
any ideas about my nvidia-glx enable problem?

---

### Post by Huzudra on 2007-04-30
help?

---

