---
title: "i destroyed my computer, please help"
date: 2006-10-21
forum: General Help
---

### Post by David123 on 2006-10-21
right now i am using my bro's computer and i just wanted to say that i destroyed my computer. i accidentally deleted the /etc/x11 file (](*,) ](*,) ](*,) ](*,) ](*,) ) and i cant start the xserver ( my graphical interface) so all i can work with is a lousy terminal. please help. i dont want to lose all my hard work i had on my computer.

---

### Post by Anonii on 2006-10-21
> **David123 said:**
> right now i am using my bro's computer and i just wanted to say that i destroyed my computer. i accidentally deleted the /etc/x11 file (](*,) ](*,) ](*,) ](*,) ](*,) ) and i cant start the xserver ( my graphical interface) so all i can work with is a lousy terminal. please help. i dont want to lose all my hard work i had on my computer.
/etc/X11 is a folder.
You removed the whole folder, or just the xorg.conf file?
Try running a 
**sudo dpkg-reconfigure xserver-xorg**
I dont know if it will help if you deleted the folder, but I think it will restore the original xorg.conf.

---

### Post by raul_ on 2006-10-21
Maybe booting from the Live CD and repairing?

---

### Post by David123 on 2006-10-21
i deleted the whole x11 folder--sorry for the bad explaing......um, how would i repair from the live CD?

---

### Post by raul_ on 2006-10-21
i'm sorry, i don't use a ubuntu install cd in a loooong time. it doesn't have a "repair installation" option or similar?
another choice is reinstalling X by the terminal with apt-get, but u would have to check with more xperienced users because i'm not sure about that one

---

### Post by David123 on 2006-10-21
there is no repair otion, but maybe i can get into my harddrive fromthe live cd. when i go to 'computer' in live cd, it displays my cd drives, and my harddrive named '54.5 g volume' but i cant explore it. any more suggestions? i want to try to somehow write only the x11 folder to my harddrive so it can boot again.thanx in advance...:)

---

### Post by raul_ on 2006-10-21
As I was saying, u can try to do ```
 apt-get remove x11
``` followed by ```
apt-get install x11
``` . i think that would work, but i don't know if it messes with your system. i don't think so though.

---

### Post by Bloch on 2006-10-21
With your computer running fom the live cd choose on the menu
System -> Adminitsration -> Disks

Then you can mount the hard dsk (Choose an access path, eg create a folder /home/ubuntu/mydisk
and click "enable" (whhich basically mounts the drive)



Then you can start moving files.
I forget what the root password is on the live CD - something simple like 'root" or 'ubuntu' - it will be stated somewhere.

---

### Post by David123 on 2006-10-21
thanx sooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo
much. my computer now works. thank you thankyou thank you thank you thank you:) :)

---

