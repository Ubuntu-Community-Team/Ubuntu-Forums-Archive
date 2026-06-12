---
title: "GRUB help"
date: 2008-07-06
forum: General Help
---

### Post by Cap'n Skyler on 2008-07-06
i need some grub help.
my win XP is in it's place,and shows up on the boot list,but i dont have the permission/option to choose it.i have seen this on other live cd's and ubuntu installs,where i get a boot screen and have options but it is set so i cant choose any but the default.
i am going to the other comp and wipe and clean it up,and then i want to get a new ubuntu(or save the good one i have there) and make it so i can choose which of the two to boot.
  i have the Q and K GRUBEditor and that is great,but i dont see where i can change the option to allow me to choose which OS to boot.


thnaks all who can help :P:guitar:

---

### Post by red_team316 on 2008-07-06
I've had this problem in the past. I believe it was due to customizing GRUB with fancy backgrounds and colors and such. I manually edit the menu.lst myself now and have had no such problem. 

Mine would show the list of OS'es but yet would not show the highlighted item change when I hit the up and down keys. Is this what you are experiencing?

---

### Post by AndyCee on 2008-07-06
> **Cap'n Skyler said:**
> but it is set so i cant choose any but the default.


Can you expand on this? When Grub loads, you can see the other options but can't select them? The highlight doesn't move?

I used a boot-menu editor to repair a Grub boo boo I made, and it fixed it at the expense of making a new boo boo. Fortunately, I could fix that one.

---

### Post by Cap'n Skyler on 2008-07-07
yes on both--i can see them but i cant choose any--it just boots the default ubuntu

---

### Post by Cap'n Skyler on 2008-07-07
i am currently deleting from the HD stuff i dont need and haphazard (me) partitions.then going to re install 'buntu and then try to get the grub all sorted out.

---

### Post by falcon61102 on 2008-07-07
Have you tried just re-installing the GRUB?  Might save you a little work.

---

### Post by Cap'n Skyler on 2008-07-07
> **falcon61102 said:**
> Have you tried just re-installing the GRUB?  Might save you a little work.
i have not--yet.i think my issue is in the chainloader.and in the part that is only allowing the default choice to boot.any suggestion on how to make it so i can choose what i want from the boot screen?

---

### Post by Cap'n Skyler on 2008-07-07
Bueller?  anyone?:popcorn:

---

### Post by falcon61102 on 2008-07-07
Lol... sorry, but other than re-installng your GRUB and then updating, I have no idea.

---

### Post by Cap'n Skyler on 2008-07-08
i *believe* my issue is in the lsi files and the chainloader.
i do know GRUB will let you do for example,10 different distros on 10 different partitions,and it will do it.i saw somewhere a guy had 100 linux distros on his comp and was sharing/showing off LOL that grub could do it.
  si i seek how to "unlock" the other choices,and set the chainloader up.

---

### Post by red_team316 on 2008-07-08
Yea, the link you are referring to I have in my sig. There should be a part in there on going into a terminal and setting up grub. Thats your best bet. Once you have a clean grub, your highlighting should work again. Other than that, Windows tend to be a little more complicated than others. Look at his XP entry, I know you will need to use the makeactive and map options. His howto is truely a great read. It taught me alot.

---

### Post by Cap'n Skyler on 2008-07-08
well thanks!!
and i found some other options to try,and to keep around till i can get the grub all fixed.i have this super grub disk ISO i can supposedly use.i'll post back about how it went.i suppose i can also put grub on a thumbdrive and leave it in the back of my computer and se how that goes.
 i'll post back soo.
i did think it was a good idea for us newbs to have some rescue/boot/help cd iso's.i made a cd of Gparted and of the super grub disk.if you are new to linux it might be good to have these around in case you need back into windows or if you have to obiterate some odd partitions as well.

BBL:popcorn:

---

