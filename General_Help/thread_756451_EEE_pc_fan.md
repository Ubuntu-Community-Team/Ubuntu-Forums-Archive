---
title: "EEE pc fan"
date: 2008-04-15
forum: General Help
---

### Post by MrChezedoodle on 2008-04-15
hi, i'm compleatly new at this kinda stuff, but i just got an EEE pc and i put ubuntu on it.  Everything runs fine, but the fan runs all the time! i tried searching for ways to fix it and have been looking for two hours, and i don't understand any of this stuff!  is theyere anyone who can explain it to me in simple terms on how to get the fan to automaticly shut off when it's cool enough?  any help will be apreciated.   

if it helps i did run acpi -t and got 56 degrees celcius.  ALso i tried the pwmconfig, but it says that there aren't any sensors found. 

This bugs me because i reinstalled ubuntu for the second time now, i messed up my partition the last time. 

if worse comes to worse i could always just go to windows i guess, but thats a last resort.

---

### Post by nicedude on 2008-04-16
Hey man here is the link you are looking for, 

[http://forum.eeeuser.com/viewtopic.php?pid=179607](http://forum.eeeuser.com/viewtopic.php?pid=179607)

It links to a guys program named EEECONTROL 0.2.1 - which is descibed as follows
"This Programm can control Fan and FSB and view the current status of it, its a gui for the eee.ko modul (from Andrew Tipton) a compiled version of eee.ko 0.2 is included in this deb." 

I read what it does and it lets you set the temp at which your eeepc fan will shutoff or slowdown.

You also might want to look into eeebuntu, which is a version of ubuntu made just for the asus eeepc. you can get more info and download it here -> [http://www.eeebuntu.org/](http://www.eeebuntu.org/)     Even if you stick with your current Ubuntu install they should be able to help you tweaking the eeepc since its what they work on doing at that site. Also I believe the eeebuntu distro comes pre setup for your Wireless driver as it applies to wardriving using kismet, aircrack, wireshark etc. So if you were wanting to do any wifi wep/wap cracking it might be easier for you to get set up and running.

Anyway whatever you choose to don't do it with Winblows. XP takes more hardware horse power for given tasks than linux does and the eeepc isn't built with many horses to begin with, its not meant to be a laptop replacement, its a specialized system that is great for what it was designed for (webrowsing, email, wireless networking).

well best of luck with your eee and if you need help installing that program above you can PM me and I will try to help you to do it.

---

### Post by ibuclaw on 2008-04-16
Another team who has ported Ubuntu to the Eee PC can be found [here.]("http://ubuntu-eee.tuxfamily.org/index.php5?title=Quick_Start")

They infact use a [script]("http://ubuntu-eee.googlecode.com/files/ubuntu-eee_v1.0.tar.gz") that fixes ubuntu so it works smoothly with the Asus Eee PC.

List of fixes is found [here.]("http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_use_the_ubuntu-eee_script")

Here is the money shot:
[IMG]http://ubuntu-eee.tuxfamily.org/images/Ubuntueee.png[/IMG]

Good luck on your quest!

Regards
Iain

---

### Post by MrChezedoodle on 2008-04-16
yo u guys r the best!  thank you so much


i'll try it in a couple of days cause i'm bussy i'll let you know how it goes


yeah i instaled some eeebuntu rip off it looks like from some fourm i found and t ran ok.  It was just ubuntu with the scripts built into the installation. It worked great until i screwed up a display setting and coulding fix it, so i just reinstalled from regular ubuntu and used the ubuntu scripts for the eee pc. that eeebuntu.org looks really interesting i'm gonna take a look at that.

thanks again for the help and if u ever are thinking about getting this laptop, i'd say go for it.  It's really convenient.  

peace

---

### Post by MrChezedoodle on 2008-04-20
yo guys thanks so much! u lead me to forums that i did a bit of searching on and i found the answer.  

All i needed to do was pull out my battery and hold the power button to drain the capacitors.  

thanks guys

---

