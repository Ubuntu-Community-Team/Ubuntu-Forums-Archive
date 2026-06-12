---
title: "Installting a emeral Theme on uBuntu"
date: 2008-06-19
forum: General Help
---

### Post by Rishabhsood on 2008-06-19
I am stuck over here
I downloaded this emerald theme, But cant figure out how to install it.
[http://www.gnome-look.org/content/show.php/Die+Hard+4.0+-+Matthew+Farrel%27s+theme+(E?content=66714](http://www.gnome-look.org/content/show.php/Die+Hard+4.0+-+Matthew+Farrel%27s+theme+(E?content=66714)

I read various tutorials and installed Emerald Theme Manager, I imported the theme into the manager, but now I cant apply that theme, I have no option to apply this theme..

Guys can you help me out?

Will be really thankful to you guys if you can help me out. I really love this theme a lot :D

:(

---

### Post by overdrank on 2008-06-19
> **Rishabhsood said:**
> I am stuck over here
I downloaded this emerald theme, But cant figure out how to install it.
[http://www.gnome-look.org/content/show.php/Die+Hard+4.0+-+Matthew+Farrel%27s+theme+(E?content=66714](http://www.gnome-look.org/content/show.php/Die+Hard+4.0+-+Matthew+Farrel%27s+theme+(E?content=66714)

I read various tutorials and installed Emerald Theme Manager, I imported the theme into the manager, but now I cant apply that theme, I have no option to apply this theme..

Guys can you help me out?

Will be really thankful to you guys if you can help me out. I really love this theme a lot :D

:(

Hi and after you have imported it to emerald are you able to select the theme? If so then have you try emerald --replace using the alt, F2 keys. This will refresh emerald and should display the theme.

---

### Post by Rishabhsood on 2008-06-19
After I imported the theme.. I'm not able to select the theme

[IMG]http://img294.imageshack.us/img294/1484/screenshotvg3.png[/IMG]

Where should I type emerald --replace ? when I press Alt+ f2 , it brings in a window to run applications. 

It is displaying the theme but letting me select it..

i can emerald --replace in terminal I had to wait for about 5 mins but still nothing happened.

---

### Post by ad_267 on 2008-06-19
In that window type "emerald --replace" and run it. Emerald is an application you are running, and replace is an option you're running it with. You can permanently set the window decorator to emerald using the compizconfig-settings-manager.

---

### Post by Rishabhsood on 2008-06-19
Sorry, but cant understand
Which window you talking about..

Ran it in terminal again nothing happens..

---

### Post by overdrank on 2008-06-19
> **Rishabhsood said:**
> Sorry, but cant understand
Which window you talking about..

Ran it in terminal again nothing happens..

Hi and using th alt, F2 keys brings up the run application and that is where you enter the command emerald --replace.
To ad to ad_267 you have to be running compiz to use emerald.

---

### Post by ad_267 on 2008-06-19
> **overdrank said:**
> Hi and using th alt, F2 keys brings up the run application and that is where you enter the command emerald --replace.
To ad to ad_267 you have to be running compiz to use emerald.

Yeah from that screenshot it doesn't look like you're using Compiz, so you will need to enable that first. You can either press Alt F2 and run "compiz --replace" or go to System - Preferences - Appearance - Visual Effects and set them to Normal, Extra or Custom.

Giving this a read is probably a good idea before you go any further: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Edit: Haha didn't see that link was already in Overdrank's sig.

---

### Post by Rishabhsood on 2008-06-19
When I click normal or extra.. this thing comes up

[IMG]http://img246.imageshack.us/img246/8942/screenshot1rn0.png[/IMG]



When I rebooted my PC, My Screen resolution became.. 640*480 Now I cant chnage it..

---

### Post by overdrank on 2008-06-19
Hi and review the sticky at the top of this forum
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
And use compiz-check and other tips to help you and post back if you have any issues. Good luck!
Edit just read your edit and you can use the alt, F2 keys again and use this command ```
gksu displayconfig-gtk
```
and adjust your resolution. Do you have a nvidia graphics card?

---

### Post by Rishabhsood on 2008-06-19
Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]



And I checked using gksu displayconfig-gtk

It doesnt let me change resolution.

---

### Post by ad_267 on 2008-06-19
What video card do you have?

---

### Post by Rishabhsood on 2008-06-20
Now when I rebooted my PC..

termal was starting up.. I had to format my laptop

I still wanna use that theme..

BTW my Video Card is \Intel® Graphics Media Accelerator X3100

[http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/1090709-1116637-1123071-1123071-1123071-81136593-81818817.html](http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/1090709-1116637-1123071-1123071-1123071-81136593-81818817.html)


Can any one do it for me using Remote desktop? :(

---

### Post by ad_267 on 2008-06-20
I'm not sure if you can run Compiz with that video card. Can you open a terminal by going to Applications - Accessories - Terminal and type "compiz --replace" and post the output here.

---

### Post by Rishabhsood on 2008-06-20
Last time also I did the same.. and my Screen resolution became 640 * 480 and wasnt able to change, so there is no way I can install that theme :(

---

### Post by Forlong on 2008-06-21
Please post the whole output of Compiz-Check.

---

### Post by Rishabhsood on 2008-06-21
> rishabh@rishabh-laptop:~/Desktop/rkhunter-1.3.2$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y
rishabh@rishabh-laptop:~/Desktop/rkhunter-1.3.2$ 

.

---

### Post by Forlong on 2008-06-21
OK, now try again.

---

### Post by Rishabhsood on 2008-06-21
After reboot


rishabh@rishabh-laptop:~$ '/home/rishabh/Desktop/rkhunter-1.3.2/compiz-check' 

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

rishabh@rishabh-laptop:~$

---

### Post by ad_267 on 2008-06-22
Now run "compiz --replace" and see if it works.

---

### Post by Forlong on 2008-06-22
The best thing now is going to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* and choosing Extra
Then you should be certain, whether it's working or not.

---

