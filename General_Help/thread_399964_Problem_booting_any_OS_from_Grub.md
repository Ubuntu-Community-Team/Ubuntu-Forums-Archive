---
title: "Problem booting any OS from Grub"
date: 2007-04-02
forum: General Help
---

### Post by aricw15 on 2007-04-02
Hello,

I'm fairly new to using Linux and in my quest to make my grub boot look appealing rather than the simple black and white I was editing my /boot/grub/menu.lst file attempting to change the splash image.  What happened was that I added a line that pointed to the new splash image as:

splashimage=(hd1,1)/boot/grub/splash.xpm.gz

Now I realized upon boot up that I had written the hd1,1 incorrectly and I believe it should be hd0,1 now when grub boots up I get this error:

failed to read splash image ((hd1,1)/boot/grub/splash.xpm.gz)
press any key to continue...

now when i press the key, I get the grub boot menu but when I select any of the options displayed, the screen goes blank like its trying to load, and then suddenly restarts and I go through the same thing all over again.  I cannot access any OS. I have XP and Ubuntu installed currently.  Anyway, is there anyway I can get back into ubuntu and either remove that line or edit it.  Thanks, any help would be greatly appreciated.

---

### Post by confused57 on 2007-04-03
See this link for mounting your root partition & editing grub using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by aricw15 on 2007-04-03
thanks, Ill give that a try when I get home and can find my cd.

---

### Post by aricw15 on 2007-04-03
Thanks alot, worked the very first time.

---

### Post by alessandrop65 on 2007-04-07
Perfect... I did a newbie mistake and did not want to reinstall. That fix worked like a charm!!!

Cheers,
alex

---

