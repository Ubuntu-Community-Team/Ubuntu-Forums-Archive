---
title: "Ubuntu REALLY slow and Unstable"
date: 2008-04-09
forum: General Help
---

### Post by smartygoldenfish on 2008-04-09
the main reason why i installed ubuntu was that it was a Stable and faster than Windows.
however slowly i am feeling my Ubuntu 7.10 is much slower than even my Windows xp!
it takes 1.5 mins to boot up while xp boots in 45 secs flat
when i click on firefox in ubuntu it really takes nearly 10-15 seconds to open!
 browsing folders in Nautilus is also FAR slower than Windows xp. Why!

To add fuel to fire, ubuntu has really unstable! really..
when i click on BACKGROUND AND EMBLEMS in nautilus and try changing the background by patterns or my custom images..the SYSTEM ALWAYS FREEZES..my mouse keeps moving but the system freezes..i remember my Windows when ctrl alt del worked as a Saviour but here i just have to turn off power! i get then GRUb errors and then it takes hours to correct them!

Yesterday i clicked on Open New Tab in Firefox and system froze! Stable? all my data gone!
:confused:
see thats a very bad thing to say to reinstall Ubuntu if you thinks so because i have done it 3 times already. 
This rythmbox is far behind from Windows Media Player. Totem opens in hours.

see this is not a sarcastic message..i really loved ubuntu..even kept it tag line for my orkut profile
but really theres a problem.
Also i have enabled some of Compiz effects from Compiz config..but not all to keep my system fast..and if i bychance enable that Cube effect! My GOD! ubuntu works like DOS ..one app a time..so sluggish that even a hanged Windows 98 will appear faster.
The funniest fact is that this all has started not suddenly..but slowly from beautiful to ugly.
I have been using Ubuntu for last 90 days.
compiz,wine,emrald,screenlets,---> only these are installed.

Can you help...see my signature for my computer config...man its core 2 duo! is 512 MB ram too low for ubuntu like for vista!

---

### Post by balaknair on 2008-04-09
Compiz+Emerald+Screenlets with 512 MB RAM is not a good idea. Gnome 2.2 is itself a huge memory hog. Screenlets can really hog a lot of memory especially if you have a lot of them running. You have an integrated graphics card with 128 MB video RAM, which means that it gets taken out of your installed RAM(so your effective RAM is only 384 MB because your graphics card is using 128 MB).
 I strongly advise upgrading your RAM(add 512 MB or better if you want all the bells and whistles that Compiz + Screenlets bring).
 If you want to see if Compiz and Screenlets are the reasons for the poor performance, Check how much memory is being used in System Monitor, then turn off compiz(Alt+F2---> "metacity --replace") and screenlets(Screenlets manager---> Close all screenlets) and restart X server(Ctrl+Alt+Backspace, or log out and choose  Restart X server at log in options). Now check system monitor again and see how much memory is used.
If you don't want to get more RAM, increasing swap file size with Gparted is an option but far less effective.

PS- if system hangs, instead of turning off the power try restarting X with ctrl+alt+backspace. You'll lose data, but you're less likely to get Grub errors.

Firefox 2 also uses up a lot of memory, and more so if you have a lot of add-ons running. Most of these issues are fixed in FF3 though(FF3 beta5 is out, you could switch to that if you want for now, though you won't be able to use many add-ons since they are incompatible with FF3). 

To speed up application start up, install preload(sudo apt-get install preload), it'll learn your application preferences over time and load the libs into memory on start up so  your apps will start faster. But again, this will take up a lot of RAM, I'd recommend at least 1 GB RAM.

---

### Post by Belak on 2008-04-09
I'd reccomend upgrading your ram. 1024 would be my reccomended amount but you might not need it.

Compiz is a system resource killer, but wine is even worse. If I were you, I'd try a virtual machine (I like VirtualBox) to run your windows apps.

One shortcut that you may have to use: In place of manually rebooting, press CTRL-ALT-BACKSPACE
This will restart your session and send you to the login screen.

I'm running a 1.6 GHz single core with a 1024 chip and a 256 chip of ram. I'm running compiz and a virtual machine as well.

I wish you luck.

---

### Post by balaknair on 2008-04-09
And if you don't want to upgrade your hardware, you can also try installing XFCE, which is lighter on resources than Gnome and KDE.
sudo apt-get install xubuntu-desktop

If you find nautilus too slow(I hate Nautilus too), you can use another file browser(I use Konqueror, though Thunar would probably be lighter on resources), there's an excellent guide at psychcats by aysiu, and you could check out other tips while you're there.
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by domace on 2008-04-09
I have a less powerful computer than you but I have no problems accepts for fire fox being slightly laggy. trying looking at your processes to see if there is one in the back ground consuming alot of memory 
--------------------------------------------------------------------------------------------------------------
system specs-
dell optiplex gx 150
512 ram and its my max ram lol
1.1 ghz p3 processor--not over clocked-yet
64 mb video card
dvd rw drives ect...
everything about my pc is good accept for the max ram part and processor and my mother board
only take copper mine processors and i don't think there are p4 copper mines 
any suggestions so i can speed up my Ubuntu as well one not buying a new  pc 
btw i run wowc on ubuntu at a decent fps and its a llaggy but worth it

---

### Post by russo.mic on 2008-04-09
I'm looking at the specs of this computer and I have to say, I somehow doubt this thing isn't capable of running Ubuntu and making it a pleasant experience.  I would almost recommend a reinstall, as I've had this problem with bad downloads of OS before.  I.E., consider redownloading the ISO, and burn at a slow speed, make sure to do the MD5, and install from there.

Just my thoughts!
Good luck!
Russo

---

### Post by R6V2 on 2008-04-09
Hmm, I'm using a 8 year-old comp, that has worse computer specs than you, and Ubuntu 7.10 runs super-fast and never freezes. I would redownload the .iso, burn it at the lowest speed, and try again.

I wish you luck in your problems.

---

### Post by smartygoldenfish on 2008-04-11
> **balaknair said:**
> Compiz+Emerald+Screenlets with 512 MB RAM is not a good idea. Gnome 2.2 is itself a huge memory hog. Screenlets can really hog a lot of memory especially if you have a lot of them running. You have an integrated graphics card with 128 MB video RAM, which means that it gets taken out of your installed RAM(so your effective RAM is only 384 MB because your graphics card is using 128 MB).
 I strongly advise upgrading your RAM(add 512 MB or better if you want all the bells and whistles that Compiz + Screenlets bring).
 If you want to see if Compiz and Screenlets are the reasons for the poor performance, Check how much memory is being used in System Monitor, then turn off compiz(Alt+F2---> "metacity --replace") and screenlets(Screenlets manager---> Close all screenlets) and restart X server(Ctrl+Alt+Backspace, or log out and choose  Restart X server at log in options). Now check system monitor again and see how much memory is used.
If you don't want to get more RAM, increasing swap file size with Gparted is an option but far less effective.

PS- if system hangs, instead of turning off the power try restarting X with ctrl+alt+backspace. You'll lose data, but you're less likely to get Grub errors.

Firefox 2 also uses up a lot of memory, and more so if you have a lot of add-ons running. Most of these issues are fixed in FF3 though(FF3 beta5 is out, you could switch to that if you want for now, though you won't be able to use many add-ons since they are incompatible with FF3). 

To speed up application start up, install preload(sudo apt-get install preload), it'll learn your application preferences over time and load the libs into memory on start up so  your apps will start faster. But again, this will take up a lot of RAM, I'd recommend at least 1 GB RAM.

i really appreciate the responses but tell me why should i go for 512 mb ram!
see ubuntu+emrald+screenlest + some artistic mind like mine will envy Vista Users
and when my frnds saw my desktop they got mad! However the sluggishness resembles to Vista!
Why should i choose Linux then at all if its little modding makes it so much resource hungry!
512 MB ram was a norm 6 months ago...but why should it becomes too less so early! 
Also till yesterday internet was working fine in Ubuntu but today..yes..its disappeared! I saw all proxy settings but nothing! And i promise that i didnt change an inch of hardware or software and got my internet not working.
However my main worry is that why my Ubuntu is not working well..is emerald+screenshots+compiz is so lethal..because people with so low configuration (compared) run it seamlessly.
And yes i have removed Wine and set effects to "exciting"
 Then too when i clicked on network proxy and edited some values it just got hanged..thanked to ctrl alt bkspce i didnt turn it off directly.
 My Ubuntu 7.10 checksum is correct
Please tell me should i completely remove ubuntu and wait for Hardy? or is fedora/opensuse waiting for me?

---

### Post by roaldz on 2008-04-11
> **smartygoldenfish said:**
> i really appreciate the responses but tell me why should i go for 512 mb ram!
see ubuntu+emrald+screenlest + some artistic mind like mine will envy Vista Users
and when my frnds saw my desktop they got mad! However the sluggishness resembles to Vista!
Why should i choose Linux then at all if its little modding makes it so much resource hungry!
512 MB ram was a norm 6 months ago...but why should it becomes too less so early! 
Also till yesterday internet was working fine in Ubuntu but today..yes..its disappeared! I saw all proxy settings but nothing! And i promise that i didnt change an inch of hardware or software and got my internet not working.
However my main worry is that why my Ubuntu is not working well..is emerald+screenshots+compiz is so lethal..because people with so low configuration (compared) run it seamlessly.
And yes i have removed Wine and set effects to "exciting"
 Then too when i clicked on network proxy and edited some values it just got hanged..thanked to ctrl alt bkspce i didnt turn it off directly.
 My Ubuntu 7.10 checksum is correct
Please tell me should i completely remove ubuntu and wait for Hardy? or is fedora/opensuse waiting for me?
You don´t have to wait for hardy, you can install it right now! It´s ready in 13 days, so it´s as good as stable:) I´m running it for a while now, and I must say that it´s quite better for me:)
If you don´t want to switch to hardy, you should install a light-weight window manager, like xfce/fluxbox or maybe enlightenment.  If that doesn´t work, you can always try another distro. 

Oh and btw, 512 megs of ram was a norm 4 years ago! 1 gig became a norm in 2005/2006. 1 gig is normal these days. Most decent workstations come with 2 gig these days.
Roald

---

### Post by apo00 on 2008-04-11
Hi, I've used Ubuntu-Gutsy for 2 weeks and also seen it is unstable.
Sometimes the system auto restart. Sometimes the system is frozen, both mouse and keyboard. I know some hot key likes Ctrl+Alt+Backspace or Ctrl+Alt+F1 but I never can use them. The keyboard is always absolutely frozen when there is a problem. I have to push the power button (in some cases the sleep button works, in some cases the sleep button doesn't).
I'm using Compiz+AvantWindowNavigator and maybe it's the reason. But I don't want to work with poor graphic environment without them. However, can't Linux/Ubuntu manage processes like the way Window OS does? In the case some applications get error and can't responding, Window users can open Task Manager and force to end them without problems. I have never seen the situation like that in Ubuntu. Whenever some applications get errors the system become totally frozen and lost control.

---

### Post by balaknair on 2008-04-11
512 MB RAM is no longer considered the norm, it's just sufficient. You can run Ubuntu even on P-II systems with 128MB RAM, but without 3D compositing and desktop enhancements if you want a responsive system. Compiz, Emerald, Screenlets etc aren't lethal, but they do require a lot of system resources. You don't really have 512 MB RAM available if you're using the integrated graphics since as I mentioned the video card hogs 128MB of the RAM. Irrespective of how powerful your CPU chip is, your system performance will suffer the lack of RAM- the MB is just as important as the GHz.
There could be many little things contributing to your decreased system performance, and inadequacy of RAM is one of them. For example if you tweaked the kernel, you could perhaps improve system performance a fair amount, but at the risk of breaking some apps or worse trashing your install. For eg. if you're using the 64bit kernel, it can improve utilisation of CPU and RAM(DDR2) resources, but some applications like flash on FF and some hardware functions like sound cards, USB, may not work correctly since they were written for 32bit and may need to be patched further.
So if you're using 64bit, that could be one source of trouble, especially if you have some program that requires 32bit libraries.
Now I can't diagnose what the problem is in your PC without a lot of HW ans SW config details(and even if I did get those details, I probably wouldn't be able to figure it out, my knowledge level here is pretty basic). I only made those suggestions because in my experience, these are the most likely causes and the most useful/effective remedies.

I hope you are able to resolve your problems, and everyone here at Ubuntuforums will help you if they can.
Wishing you luck

---

### Post by picopir8 on 2008-04-11
> **smartygoldenfish said:**
> i really appreciate the responses but tell me why should i go for 512 mb ram!
see ubuntu+emrald+screenlest + some artistic mind like mine will envy Vista Users
and when my frnds saw my desktop they got mad! However the sluggishness resembles to Vista!
Why should i choose Linux then at all if its little modding makes it so much resource hungry!
512 MB ram was a norm 6 months ago...but why should it becomes too less so early! 


Open a terminal and run 'top' to determine what is consuming all your resources.  I suspect one program is the cause and removing that program will improve your performance.  

I also second the recommendation to run xfce instead of gnome.  It is less resource intensive and runs a lot nicer on resource limited machines.

And yes, you may need to turn off all the glitter.  While that may make you envious of Vista, Vista still wont run on that computer.  All versions of vista (except for the bland home basic version) require 1GB of RAM.

---

### Post by smartygoldenfish on 2008-04-12
> **roaldz said:**
> You don´t have to wait for hardy, you can install it right now! It´s ready in 13 days, so it´s as good as stable:) I´m running it for a while now, and I must say that it´s quite better for me:)
If you don´t want to switch to hardy, you should install a light-weight window manager, like xfce/fluxbox or maybe enlightenment.  If that doesn´t work, you can always try another distro. 

Oh and btw, 512 megs of ram was a norm 4 years ago! 1 gig became a norm in 2005/2006. 1 gig is normal these days. Most decent workstations come with 2 gig these days.
Roald
in india..it became 6 months back..1 gb nw..u r partially correct
> **apo00 said:**
> Hi, I've used Ubuntu-Gutsy for 2 weeks and also seen it is unstable.
Sometimes the system auto restart. Sometimes the system is frozen, both mouse and keyboard. I know some hot key likes Ctrl+Alt+Backspace or Ctrl+Alt+F1 but I never can use them. The keyboard is always absolutely frozen when there is a problem. I have to push the power button (in some cases the sleep button works, in some cases the sleep button doesn't).
I'm using Compiz+AvantWindowNavigator and maybe it's the reason. But I don't want to work with poor graphic environment without them. However, can't Linux/Ubuntu manage processes like the way Window OS does? In the case some applications get error and can't responding, Window users can open Task Manager and force to end them without problems. I have never seen the situation like that in Ubuntu. Whenever some applications get errors the system become totally frozen and lost control.
I miss task manager .. Microsoft has *some brain*
> **balaknair said:**
> 512 MB RAM is no longer considered the norm, it's just sufficient. You can run Ubuntu even on P-II systems with 128MB RAM, but without 3D compositing and desktop enhancements if you want a responsive system. Compiz, Emerald, Screenlets etc aren't lethal, but they do require a lot of system resources. You don't really have 512 MB RAM available if you're using the integrated graphics since as I mentioned the video card hogs 128MB of the RAM. Irrespective of how powerful your CPU chip is, your system performance will suffer the lack of RAM- the MB is just as important as the GHz.
There could be many little things contributing to your decreased system performance, and inadequacy of RAM is one of them. For example if you tweaked the kernel, you could perhaps improve system performance a fair amount, but at the risk of breaking some apps or worse trashing your install. For eg. if you're using the 64bit kernel, it can improve utilisation of CPU and RAM(DDR2) resources, but some applications like flash on FF and some hardware functions like sound cards, USB, may not work correctly since they were written for 32bit and may need to be patched further.
So if you're using 64bit, that could be one source of trouble, especially if you have some program that requires 32bit libraries.
Now I can't diagnose what the problem is in your PC without a lot of HW ans SW config details(and even if I did get those details, I probably wouldn't be able to figure it out, my knowledge level here is pretty basic). I only made those suggestions because in my experience, these are the most likely causes and the most useful/effective remedies.

I hope you are able to resolve your problems, and everyone here at Ubuntuforums will help you if they can.
Wishing you luck

Thanks!
I am sure i had everything 32 BIT..i pressed on it while getting iso.
 I agree 512 MB RAM=no spl effects for you
But tell me one thing has processor power become so obselete! i have a core 2 duo (2 cores one 1 ...2 cpus in one...Intel)

Then why is intel making quad to core and that 8 core thing!
lets all get a p4 with 10 GB ram and finish the performance issue for next 3-4 years!

to fix my system..i installed kubuntu and removed ubuntu completely
i feel now i m on a boeing 747
its live cd ran faster than the installed Ubuntu!

it can not be possible that i can not configure my system (now kubuntu..fast but then too..as past can haunt back) for using both cores effectively..change kernel..oor anything else.
Then i will get compiz again and convert it to a OS superior to Vista (i know kubuntu sheduling is better)
send it to REDMOND...bill gates will cry.   ;)

Thanks in advance

---

### Post by harrybazeegar on 2008-04-12
If you want a REALLY fast system and you dont care about the looks then go for Xfce Destop Environment.

It is Reeeally light, loads fast, works fast and IS fast!
===================================
If you care about looks and dont want to be too modest then go for GNOME. 
===================================
I really dont know much about this, but I have heard (and seen) that KDE looks way better than GNOME with all the right themes, but I have never come to like the look and feel of KDE. 
But you _should_ try KDE once... it will give you perspective.
===================================

BTW running Compiz, wine _and_ screenlets all together on GNOME with only 512M of memory to spare is a really bad idea...

---

### Post by harrybazeegar on 2008-04-12
if you want a task manager... try 'gnome-system-monitor', or Applications->System Tools->System Monitor

If you are a command line freak (which you probably are *not* ) you might want to see what the '*ps*' command does... used along with '*grep*' this can be as powerful as a system monitor :)

---

### Post by pbpersson on 2008-04-12
My system started running slower and slower and then hanging

I did a search on this forum for posts like "system freezes" and found a useful guide.  It told me to:

1.  Delete and re-create my swap space in case it was corrrupted
2.  Delete all the folders in /tmp
3.  Install the lastest version of Envy and use it to install the latest driver for my ATI card

I have not had any problems since then

Ah......I did save the instructions for the swap space rebuild:

```
Make sure you close all programs BEFORE swapoff.

sudo swapoff -a
sudo mkswap /dev/xxx9
sudo swapon -a

where xxx9 is your swap partition; such as sda5, sda6 or whatever.
```

---

### Post by roaldz on 2008-04-12
> **pbpersson said:**
> My system started running slower and slower and then hanging

I did a search on this forum for posts like "system freezes" and found a useful guide.  It told me to:

1.  Delete and re-create my swap space in case it was corrrupted
2.  Delete all the folders in /tmp
3.  Install the lastest version of Envy and use it to install the latest driver for my ATI card

I have not had any problems since then

Ah......I did save the instructions for the swap space rebuild:

```
Make sure you close all programs BEFORE swapoff.

sudo swapoff -a
sudo mkswap /dev/xxx9
sudo swapon -a

where xxx9 is your swap partition; such as sda5, sda6 or whatever.
```
 
Envy only makes things worse, doing things on the non-standard way.

---

### Post by pbpersson on 2008-04-12
> **roaldz said:**
> Envy only makes things worse, doing things on the non-standard way.

I used Envy on two machines here and they are running fine

Well....the Mint machine is not running 100% but well enough to use

I looked at the manual instructions for that and decided if I needed to do it manually, I would go out and buy a new video card and then grind the ATI Radeon 9550 into little pieces and stomp it into graphics card dust.

I'm glad that Envy came to the rescue  :)

---

### Post by roaldz on 2008-04-13
> **pbpersson said:**
> I used Envy on two machines here and they are running fine

Well....the Mint machine is not running 100% but well enough to use

I looked at the manual instructions for that and decided if I needed to do it manually, I would go out and buy a new video card and then grind the ATI Radeon 9550 into little pieces and stomp it into graphics card dust.

I'm glad that Envy came to the rescue  :)

Envy is just some script that does the dirty work. What if apt decides if it wants to update some mudules/drivers/files that envy has overwritten? Or envy deletes something that apt created? I like to keep things organized in the standard way, so there´s no automatix/envy/ubuntutweak for me:)

Roald

---

### Post by smartygoldenfish on 2008-04-13
so d moral of storyz dat>
envy works gud if u hv gud lk
kk
bt plz ans ma questn>
make kubuntu use ma dual processor to max..

---

### Post by jocko on 2008-04-13
> **smartygoldenfish said:**
> so d moral of storyz dat>
envy works gud if u hv gud lk
kk
bt plz ans ma questn>
make kubuntu use ma dual processor to max..
Something wrong with your keyboard???

To make (k)ubuntu use your dual core to the max, you really need to install the 64 bit version (at least if you have a core **2** duo or any other 64 bit cpu).
But, as you only have 312 Mb of usable ram, I think you would gain pretty much by adding more ram (I remember 3 years ago when I upgraded from 512 Mb to 1.5 Gb what a huge difference it made to the performance of windows xp on my old 1.86 GHz athlon XP. Adding 1 Gb was probably overkill, but 2*512 was only marginally more expensive than 2*256. I still use this 5 year old computer with gutsy gibbon with no performance problems whatsoever)

---

### Post by smartygoldenfish on 2008-04-13
i cant spend a buck now-a-days because of global financial crisis and rising crude oil prices and inflation here is 7.41%
i can only download free Kubuntu iso

somebody told me that you can only run 32 BIT OS bcoz u can only because in Windows in desktop properties the max color quality is 32 BIT so i can not run 64 bit things
but if that guy is wrong(he should be!) then wont i have probs in installing third party softwares on a 64 bit system? [i think you mean me to install a 64bit kubuntu]

---

### Post by jocko on 2008-04-13
The color depth of your graphics have nothing to do with what capabilities your processor have.
If your processor supports 64 bit, then a 64 bit os can make better use of your processor than a 32 bit os (but if ram is your bottleneck, you'll probably not notice any difference).
As for installing 3rd party apps there may be some problems, but there are simple solutions available for most of these. All the apps that are present in the 32 bit ubuntu repos are available as 64 bit versions (possibly with a very few exceptions). Check out the 64 bit section of the forums.
Now I'm not saying 64 bit will magically solve the problem you are experiencing with unresponsiveness and instability (but a fresh install of anything, be it 64 or 32 bit may help if the problem is due to a bad configuration or software bug). If you can't get more ram, then a less demanding desktop environment, such as xfce (xubuntu) or even gnome may be more responsive than kde.

---

### Post by smartygoldenfish on 2008-04-16
After so much huddling and fiddling i have concluded that Ubuntu is a Great Operating System.

However if you want to have Windows Vista (and better) visual effects then YOU MUST have min 1 GB RAM
*so*
*A Ubuntu capable PC* is anything...P II with 64 MB RAM
*A Ubuntu Premium (Compiz, Emrald, ScreenLets, WIne) PC* is a actually an equivalent Vista Premium stuff! But at absolutely 0.00 $ Volume Licence.

But if you want *slightly* beautiful OS..shift to KDE 4.

Thank you

---

### Post by jocko on 2008-04-16
> **smartygoldenfish said:**
> *A Ubuntu Premium (Compiz, Emrald, ScreenLets, WIne) PC* is a actually an equivalent Vista Premium stuff! But at absolutely 0.00 $ Volume Licence.

Not quite. I would **never** run vista on my 5 year old computer (1.86 GHz Athlon processor, 1.5 Gb ram, ati radeon 9600 pro 128 Mb), but it runs Ubuntu with compiz and emerald **much** smoother than it ran XP before I got rid of windows.

---

