---
title: "HOW TO: Make Ubuntu Look Like XP"
date: 2008-06-06
forum: General Help
---

### Post by Matthew Wiebelhaus on 2008-06-06
***You may be wondering why the heck you would ever want to make a linux operating system look like windows. Well the answer is really simple. Most windows users want and easy switch from windows to linux with a familiar interface. Also, if you are trying to convince older adults to make the switch they will not want to learn a totally new system at their age. So by searching threw gnome-look.org and looking threw some guides you can make your system look like XP.***

*To make your system look like XP follow the steps in the correct order.*
 
First download all the files linked to this post to your desktop.Second, Open Apperance and install the LinuxXP.tar.gz after that you will be promoted to Apply the theme and select that choice. 
Third, remove the menu bar (If you have this on your panel) and then add the main menu item to your panel.

Fourth, move startubuntu.png to **/home/*[COLOR=Red]USERNAME[/COLOR]*/Pictures**

Fifth, open your terminal and type the following command.

> gconf-editor When you execute this command a "Configuration Editor" window will open you will need to go down the list on the left to get to a certain item so do the following.

> apps > panel > objects > object_0Sixth, in the right pane check the box for Use_Custom_Icon then, right click

> custom_icon > Edit KeyIn the value box type

> ***/home/[COLOR=Red]USERNAME[/COLOR]/Pictures/startubuntu.png***Once you have entered this into the box click OK if you followed all steps correctly then you should see your icon on your Main Menu item change to a Windows Like start button with a ubuntu logo.

You can now drag your panels around and change the position of the items on the panel [U][I]to make it look more like windows.

[/I][/U][I][B][COLOR=Red]The Next Steps Are OPTIONAL and are only here to make Ubuntu look very much like windows.

[/COLOR][/B][/I][COLOR=Red][COLOR=Black]If and only if you have the firefox launcher on the panel and the evolution launcher on the panel you can do the following steps.

First move firefox.png and evolution.png to [B][I]/home[COLOR=Red][COLOR=Black]/[/COLOR]USERNAME[/COLOR]/Pictures/

[/I][/B]Second right click on the firefox launcher and click on the Icon then navigate to your pictures folder, then click ok. Once you have clicked ok you can select the firefox.png to make your firefox Icon look like Internet Explorer.

Third right click on the evolution launcher and click on the Icon then navigate to your pictures folder, then click ok. Once you have clicked ok you can select the evolution.png to make your Evolution Icon look like Outlook Express.

Fourth go to your desktop and move the trash.png to [/COLOR][/COLOR][COLOR=Red][COLOR=Black][B][I]/home[COLOR=Red][COLOR=Black]/[/COLOR]USERNAME[/COLOR]/Pictures/
[/I][/B]
Fifth on your desktop right click > create launcher. On the drop down list select Location. Then in the location text box type the following:

[/COLOR][/COLOR]> trash:///After you have entered that into the text box you can click on the default Icon and navigate to [COLOR=Red][COLOR=Black]***/home[COLOR=Red][COLOR=Black]/[/COLOR]USERNAME[/COLOR]/Pictures/ ***click OK. Once you have clicked ok you can select trash.png then click ok, and exit all dialog boxes. 

If you want to have the default XP wallpaper you can download it here and set it as your Desktop Wallpaper [http://img99.exs.cx/img99/6941/EnergyBliss.jpg](http://img99.exs.cx/img99/6941/EnergyBliss.jpg)

After you have done all of the following you should have a desktop that looks like XP and a recycling bin on your desktop just like on XP. Which should look like the following.

[IMG]http://i26.tinypic.com/4fxqwm.png[/IMG]

Original Theme Is From Here [http://gnome-look.org/content/show.php/NotXP?content=73782](http://gnome-look.org/content/show.php/NotXP?content=73782)

---

### Post by miggols99 on 2008-06-18
I like this :) I'm always getting people complaining that "Ubuntu looks strange" or "Where's the start button" I actually don't mind imitating Windows, because it really does help Windows users transition over to Ubuntu. Now I've got to get a WMP11 clone...

---

### Post by Matthew Wiebelhaus on 2008-06-18
> **miggols99 said:**
> I like this :) I'm always getting people complaining that "Ubuntu looks strange" or "Where's the start button" I actually don't mind imitating Windows, because it really does help Windows users transition over to Ubuntu. Now I've got to get a WMP11 clone...

Thank you, im glad someone appreciates my guide : )

---

### Post by Jongleur on 2008-06-19
[QUOTE : Also, if you are trying to convince older adults to make the switch they will not want to learn a totally new system at their age.]

What's with this ageism thing? I'm 68 and I've switched completely to Linux and dumped Windoze.

Age has nothing to do with computer literacy.

---

### Post by hariprs on 2008-06-20
Hi,

Try

1. Clearlooks-Luna for controls
2. LinuxXP - Window border
3. GnomeXP - Icons
4. Bliss - Wallpaper (Try google image)

---

### Post by Pabx on 2008-06-20
It looks nice , it could help people to get used to ubuntu, but I really prefer the normal look.

but still i'll try to show it to some friends and thank you!

---

### Post by pspmasterpro on 2008-06-20
Hello I'm having a problem with this you see for the startubuntu.png I dragged that to /home/pspmasterpro/Pictures/ folder and then I used the Configuration Editor and added the value "home/pspmasterpro/Pictures/startubuntu.png" to the custom_icon key but when I look at the Main menu I still see the default Ubuntu icon wonder why? Oh and I'm running Ubuntu 8.04 64-bit AMD version.

---

### Post by sstusick on 2008-06-22
Does anyone have the Windows Classic or standard icon? I am focusing on a Windows classic look and it would be complete if I just had a classic start menu icon. 

Thanks :)

---

### Post by master5o1 on 2008-06-23
> **pspmasterpro said:**
> Hello I'm having a problem with this you see for the startubuntu.png I dragged that to /home/pspmasterpro/Pictures/ folder and then I used the Configuration Editor and added the value "home/pspmasterpro/Pictures/startubuntu.png" to the custom_icon key but when I look at the Main menu I still see the default Ubuntu icon wonder why? Oh and I'm running Ubuntu 8.04 64-bit AMD version.

Check and make sure that it is infact:

"**/**home/pspmasterpro/Pictures/startubuntu.png"

NOT

"home/pspmasterpro/Pictures/startubuntu.png"

The slash is important.

---

### Post by wh0rd on 2008-06-23
Brilliant, this will cut down the Linux learning curve for users coming from the Windows world. How about we propose this for the next Ubuntu release, Intrepid Ibex?:tongue:

---

### Post by Matthew Wiebelhaus on 2008-06-27
thanks for all the comments and thank you all for helping other members I haven't been able to help much because I have infact been on Windows for awhile because im on a long trip and need some games to keep me occupied. But once I get back I will be able to help others out.

---

### Post by Matthew Wiebelhaus on 2008-06-27
> **sstusick said:**
> Does anyone have the Windows Classic or standard icon? I am focusing on a Windows classic look and it would be complete if I just had a classic start menu icon. 

Thanks :)

Also, you can try this one 

[http://gnome-look.org/content/show.php/2000+Look?content=40341](http://gnome-look.org/content/show.php/2000+Look?content=40341)

---

### Post by Hawk_AA on 2008-06-27
Hehe,

Nice guide!

I would never do this, because the only reason i switched from XP to ubuntu, was to avoid pressing start to stop the computer...:-\"

Hawk

---

### Post by Matthew Wiebelhaus on 2008-07-23
> **Hawk_AA said:**
> Hehe,

Nice guide!

I would never do this, because the only reason i switched from XP to ubuntu, was to avoid pressing start to stop the computer...:-\"

Hawk

are you sure that was the only reason :KS

---

### Post by jkyahoo101 on 2008-07-23
lol That reminds me of this video.

[http://blimptv.blogspot.com/2007/11/vista-sucks.html](http://blimptv.blogspot.com/2007/11/vista-sucks.html)

I wish I would have know about this guide 2 days ago. I made my dad's pc look like XP because I recently switched him to Ubuntu 8.04. (he was sick of the viruses XP had)

---

### Post by Matthew Wiebelhaus on 2008-08-05
I still use xp right at the moment and havent had any problems with virus in the last year or two.

---

### Post by duckfeet on 2008-08-05
I don't know.  I've made the error of trying to switch people to linux, and then they want me to spend way too much time doing the work they should be doing, when some app or another doesn't have pre-installed drivers on linux...linux is for "enthusiasts"...the same kind of guys used to like making radios, and stood outside in front of Radio Shack talking about tubes, and newfangled transistors and such...linux's not mainstream, and I hope it never gets that way, or somebody'll sell it...

Doesn't have anything to do with age...my Mom is late seventies, but the computer guy is my stepdad, and he just turned 94, but he stays on Windows XP, cuz that's what he knows...on the other hand, I'm 57 and the guys who helped me load linux, and showed--and continue to show--me, when I have problems are often older than me...

But trying to make linux "look like Windows" will just cause problems when something doesn't work, and you can't just click on an app, or put in a CD to get it working...then guess who gets to spend the late nights figuring it all out???

---

### Post by blueamcat on 2008-08-05
Awesome! If only I could get my parents to switch...thing is, most of the programs my dad uses aren't really available in Linux. :p

---

### Post by efrens on 2008-08-08
Hey thanks for the tutorial.

I am having a problem with step 6 though....

Edit:
Haha, figured it out already.


But the this thing down here I haven't yet. :D

[>> and maybe someone tell me how to create decent shapes in GIMP? Can't figure out how to at least encircle something :( haha]

Thanks.

---

### Post by Matthew Wiebelhaus on 2008-09-07
> **blueamcat said:**
> Awesome! If only I could get my parents to switch...thing is, most of the programs my dad uses aren't really available in Linux. :p

you could try wine.

---

### Post by father time on 2008-09-07
Message Deleted.

---

### Post by Matthew Wiebelhaus on 2008-10-18
> **father time said:**
> Thanks for the guide, I was looking for something like this a couple of days ago.  

Edit: For anyone having problems with adding the Start Menu Icon, there may be more than one object in the apps > panel > objects folder.  Just look around for the object that has the "key > value" pair of "object-type > menu-folder". 

Take care,

~ Father Time ~

Thanks for helping the others.

---

### Post by Methanoid on 2008-11-23
Good guide but doesnt work on a fresh install of Ibex (8.10).

First off it complains "This Theme will not look as intended because the required GTK + theme engine 'ubuntulooks' is not installed. 

Then other errors such as nothing at all in the apps > panel > objects folder

I think the idea of an XP or XP Classic look is brilliant for Ubuntu. I'm an XP user and I'd be happy to use Ubuntu as it is but my family won't be. If I can set it up to look close to XP Classic they will be happy enough (especially since they are all Firefox fans and FF on Ubuntu looks close enough).

I would hazard to suggest that someone should update this having done a FRESH install of 8.10 and then done each stage to produce the final result. I know its work but I think MANY many people would appreciate it!!!

---

### Post by Methanoid on 2009-01-23
No-one interested? I found two brilliant guides to make Ubuntu look & feel like OS X but no-one seems to have a complete and working one for Windows XP... :(

---

### Post by Roque2 on 2009-03-25
Very nice guide.

---

### Post by Roque2 on 2009-03-25
> **Methanoid said:**
> Good guide but doesnt work on a fresh install of Ibex (8.10).

First off it complains "This Theme will not look as intended because the required GTK + theme engine 'ubuntulooks' is not installed. 

Then other errors such as nothing at all in the apps > panel > objects folder

I think the idea of an XP or XP Classic look is brilliant for Ubuntu. I'm an XP user and I'd be happy to use Ubuntu as it is but my family won't be. If I can set it up to look close to XP Classic they will be happy enough (especially since they are all Firefox fans and FF on Ubuntu looks close enough).

I would hazard to suggest that someone should update this having done a FRESH install of 8.10 and then done each stage to produce the final result. I know its work but I think MANY many people would appreciate it!!!

I second the motion.

---

### Post by Slasher999 on 2010-10-30
thanks for putting this guide together. looks good! :)

tried the Trash short cut on the desktop but the only drawback is it doesn't show the different icons for full and empty. obviously won't do this as its only an icon.  shame tho!!

---

