---
title: "Wine, not enough free space on /C , what does this mean?"
date: 2007-03-02
forum: General Help
---

### Post by whee on 2007-03-02
I'm trying to do something with a windows application i'm running through Wine, but it requires quite alot of space, several GB's.
Though when i'm about to run something in the application, then an error message pops up about not having anough space on /C.
Now something like this could be easily solved in Windows, because i understand what it means in Windows, but in Ubuntu i have no drive C.
On top of that all my drives have enough free space.
So i think it might have something to do with a particular drive(space) that Wine has allocated to run Windows apps with.
Can someone explain to me how i can free space on /C ???

---

### Post by KAL9000 on 2007-03-02
Well with Wine if you look in its install folder you will see C_drive which is c: when you run wine. now im having the problem when i want to install WOW to work with wine. the install is 6GB or something god awful and i only have 3GB free on that partition. How do i make it go onto a new one. which I'm assuming will be the same answer for you post :)

---

### Post by whee on 2007-03-02
Ah i see, so this C_drive folder is basically some sort of pseudo-partition?
Then the question would probably be, how to enlarge it.
Does anyone happen to know?

---

### Post by KAL9000 on 2007-03-02
It is limited by the size of the partition the folder is on. so if that folder is on hdb1 and thats only got 2GB free then yur virtual c: can only be 2GB. what i need is a way to move the Wine install or the c_drive folder or make a d_drive folder somewhere else :P

---

### Post by whee on 2007-03-02
Well i happen to know how to do that.
Run a terminal and type: winecfg
And then go to the tab "Drives", there you can choose a different location for the c_drive directory.
Maybe i should try the same.

---

### Post by whee on 2007-03-02
PS: When i want to run some directX game through wine, do i have to install directX or does Wine have that already built in?
Does anyone happen to know?

---

### Post by KAL9000 on 2007-03-02
Lol looks like you probably answerd your own question there then. just chance the plase the folder is at onto a partition with more space.

Ive booted windows now anyway to play wow. will try it tommorow :P

Gunna have to fight with Apache and also find a decent FTP server at somepoint as well...Oh the fun of Linux.

---

### Post by whee on 2007-03-02
On Windows i used to use Filezilla Server as an ftp-server.
Version 1 and 2 were only available for windows, but the new Version 3 beta 6 is also available for Linux.

---

### Post by KAL9000 on 2007-03-02
Yea I had filezilla on thw PC untill it died and Ive just not back round to putting it on. may have alook at the linux verion tho. Being a typical windows user i hate the fact that alot of stuff is made with no GUI support. no buttons to click. its all txt editing and CLI :(

I will try the wow thing tommorow and let you know how it goes. then it's to playing with Apache and an FTP server. also need a VNC vewer. those last 3 are criticalfor a serverbox i want to make so we will see.

Thanks for the help there tho I suppose the feeling is mutual, see I do know SOMETHING :P

---

