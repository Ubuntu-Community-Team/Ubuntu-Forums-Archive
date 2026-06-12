---
title: "Issue computer starts restarts then boots up fine. xubuntu 16.04"
date: 2016-08-27
forum: General Help
---

### Post by zephar123 on 2016-08-27
HI all, been around for a long time, but rarely ever need to post on here.

I have a really strange issue on one of my clients computers. 

It starts up and gets to grub. You select the OS xubuntu 16.04 . It  look likes its goign to boot up goes to a black screen then the computer restarts.

You select the same OS again and the computer goes to a black screen just for a second and then loads up fine. Does not have this issue with windows 7 that still on the computer. Both OSes are are the same HD. 

The proccessor is a  [AMD Sempron 3850 Kabini ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819113366")
Begining to wonder if maybe this has something to do with it having AMD APU? the graphics works fine once it loads up. Might of should of done 14.04,  but this computer just for work so I figured the open source drivers would be fine. 

Anything you guys can think I should check when I go back their I would appreciate. I have never had such an odd issue. As it always boots up after the first fail and it restarting itself.[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16819113366"]


[/URL]

---

### Post by zephar123 on 2016-08-29
Ok, Figured this issue out so posting it here for anyone who may run into the same issue. 

In this case it was the AV comodo that was causing the glitch. This issue is only if you have home directory encrypted from what I can tell. As I have tested comodo in the past and never ran into this. 

issue is comodo tries to scan /home/.ecryptfs folder.

add in the setting comodo exclusions to /home/.ecryptfs*

and that should correct your issue. As it solved the issue for me.

---

### Post by RobGoss on 2016-08-29
Thanks for posting your findings for this issue I'm sure it will others with this problem

---

