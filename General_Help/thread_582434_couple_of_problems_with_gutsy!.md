---
title: "couple of problems with gutsy!"
date: 2007-10-19
forum: General Help
---

### Post by ninjaprawn on 2007-10-19
hi

im not having a smooth ride with gutsy! i tried to upgrade from fiesty to gutsy with the update manager, it seemed to go ok, but wen it was finished rebooting, the x server kept crashing after 10 seconds. it was complainin about gtk and setuid!

id already burnt a full copy of gutsy incase anythin went wrong, so just installed from the disk! that went perfectly. 

had a little look at the composite stuff, and it was quite cool! but turned it off while i played with xorg.conf for my mouse and twin x servers on 1 card!

finished this, installed obex, gftp, wine, firestarter and utorrent. then tried to turn the basic composite back on! it failed! cant get it back on now!

im guessing its still the same problem as in fiesty, that 2 x servers ruins it!

also, followed the below link, which i used to help me set up fiesty, thinking it would help with firestarter! no matter wot i do, i cant get firestarter to start on boot!
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

other than that tho, it seems a lot better. if anyone has any advice for the above problems, please tell me! i would appreciate it alot.

thanks.

---

### Post by DagMan on 2007-10-19
For firestarter, this looks wrong:
>  How to make the Firestarter GUI start automatically at startup

    * Note: Once you have setup the iptables firewall the first time using Firestarter, you do not need to have Firestarter running to be protected by the IPtables firewall (which is then always enabled in Ubuntu). Firestarter is only the GUI for changing the settings of the firewall; it only needs to be started when doing so. The following step is therefore unnecessary for most users. 

```
System -> Preferences -> Sessions -> Startup Programs -> New
Name: Firestarter --start-hidden
```



You would need to follow the instructions to edit your sudoers file 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_have_Firestarter_start_without_the_root_password](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_have_Firestarter_start_without_the_root_password)

And then it should be like this
```
System -> Preferences -> Sessions -> Startup Programs -> New
Name: sudo firestarter --start-hidden
```

---

### Post by chrishere01 on 2007-10-19
you have wine installed and working?

could you help me out with geting mine to wok?

---

### Post by ninjaprawn on 2007-10-19
i installed wine just by using add/remove.

click on applications -> add/remove -> type 'wine' in the search box (make sure u have 'all open source packages' set in the top right drop down. tick the box, press ok a few times. and ur done!
it will ask for ur password.

if once installed, double clicking a .exe doesnt work, right click the .exe -> select 'opens with' -> click 'add' -> type 'wine' -> press ok a couple of times and ur done!

---

