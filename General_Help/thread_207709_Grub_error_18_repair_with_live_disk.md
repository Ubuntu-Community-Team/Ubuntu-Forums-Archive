---
title: "Grub error 18: repair with live disk?"
date: 2006-07-02
forum: General Help
---

### Post by Declan on 2006-07-02
Hi all,

I tried to put in a grub splash screen, following instructions from gnome-look.org .  Those were...
(1) Copy the file (*.xpm.gz) to e.g. /boot/grub/
(2) Then add the following line to your /boot/grub/menu.lst:
splashimage=(hd1,0)/boot/grub/UbuntuEL.xpm.gz

Result: I now get two error messages on booting, and no access to my system.  The first message refers to not finding the splashimage (although I did put in the suggested location). The second message is more worrying: Error 18: Selected cylinder exceeds maximum supported by BIOS.

I don't see how this error is connected with my placing an instruction to include an image in GRUB.

Anyway, the computer now does not boot, which is less than convenient.

One idea was to use the live disk to attempt to delete the line that I changed.  But I don't know precisely how to gain access to /boot/grub/menu.lst .  Any ideas?

Declan

---

### Post by Herman on 2006-07-02
Sure you can do that,* Click Here[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")* for illustrated how-to.
Good Luck with it, Regards, Herman :D

Edit: Here's all I have on splashimages too,* [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")* just in case it helps. I don't see what you did wrong either though.
Here's mine: splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz
Is your Ubuntu the first partition on your second hard disk?
Mine is the second partition on my first (and only) hard disk.
Also my image file is just in /boot, but that probably won't make any difference.

---

### Post by Declan on 2006-07-02
Excellent.  You have been very helpful!  Turns out I had figured out all of that except the ext3 part.
That worked perfectly. Thanks.

Declan


[PS: Is there an extra "/" in your cd instruction here (ubuntu@ubuntu~:$ cd /media/ubuntu//boot/grub/)?]

---

### Post by Herman on 2006-07-02
> Is there an extra "/" in your cd instruction here (ubuntu@ubuntu~:$ cd /media/ubuntu//boot/grub/)?]Yes, you are correct, there is an double '//' in my command. It doesn't seem to make any difference ,just tested it with a single and double slash and it works just as well either way. It just seemed like a good idea to me, because we are going from one system to another. I'm not sure which way is strickly correct, I will look into it when I get some time. The double slash is sometimes needed for networking, but may be superfluous here. I'm not an expert, so I'll check on that and see if I can find out for sure. (Unless someone can comment on that here). Thanks. :D  Regards, Herman

---

### Post by teaker1s on 2007-03-02
excellent

---

