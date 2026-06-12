---
title: "please help me...i want ubuntu"
date: 2007-04-04
forum: General Help
---

### Post by river_plate_2005 on 2007-04-04
alrite this is where it started, 
i have had it with windows and wanted to give linux a try, specially after looking at videos on youtube of ubuntu with beryl. 

When i got into ubuntu it was very different then xp and i found myself lost, i knew it would take me time to adjust but i am willing to take this challange. However my internet didnt work, and this just messed everything up as i couldnt look up anything when i needed help. So i have xp right now and i am going to install two OS on my system (ubuntu and xp). I really need help on how to set up my wireless internet connection on ubuntu.
I have a wireless usb thing that connects to any infastructure that is in range and works well under xp. [IMG]http://i.expansys.com/i/b/b125875.jpg[/IMG] like this one. I have the installation cd but its for windows. 
Can anyone please help me with this? and on the computer i usually only use mirc, file sharing, play few games on the internet like flash and stuff, msn, youtube, i probably need winzip or winrar ...you know just normal things...can i do all this on ubuntu??
and also when i installed ubuntu there were a lot of folders in file system i thing if i remember it well or file structure. What are those for? or any tips on what to do after i install ubuntu or any good features?
Thanks a lot guys,
Hope i will be using ubuntu soon

---

### Post by spankymasterc on 2007-04-04
U say u never tried ubuntu? well a good way to start is looking here [www.ubuntuguide.com](www.ubuntuguide.com) tells you everything and installing ubuntu is a breeze but installing apps and such is a hassle somethimes... but when u get everything working man i tell you its awsome.... well i dont know about the usb but winzip is not winrar its rar and its pretty easy to compile now and i dont know bout mirc but IRC client is replaced by GAIM it uses msn,yahoo, IRC, Aim , and a few more all on one client AWSOME! flash well i dont know about that but i will look around im pretty sure theres a workaround for that You tube def works and thats about it.... i will try to look around for help on the wireless prob of yours if u want u could add me to msn messenger, yahoo , or aim?

[email]Spankymasterc@hotmail.com[/email] (msn)
spankymasterc (aim)
spankymasterc666(yahoo) 

and the dual boot well be careful! i know what im telling u i could help you on that if you want well ;:::Cheers::: hope i helped

one last thing u can also always run a Virtual machine on linux and im def willing to help :D and then u could run xp apps on linux!

---

### Post by river_plate_2005 on 2007-04-04
thanks a lotttttttt.... :D :D :D :D :D
i added you to my msn...hope to talkt o u soon and yes i would really like to talk to someone and learn getting into ubuntu as i think that will be way easier and help me understand things clearer... 
so jus to start off do i need to create two partition? one for xp and one from ubuntu.?

---

### Post by kevinlyfellow on 2007-04-04
It's great that your willing to try out linux.  Unfortunately, hardware vendors are reluctant to make linux drivers.  We need to do things the hard way until that changes, so expect to get your hands dirty.

What your going to need to do is install a program called ndiswrapper, which takes wireless drivers built for windows and makes them work for linux.  You then will need to locate your wireless driver and then ask ndiswrapper to use it.  [I hope you know where the terminal is!]("http://www.psychocats.net/ubuntu/terminal")  BTW, we use commandline ALOT, not necessarily because we need to, but because we like to.  It makes life so much easier ;-)  I'm writing this under the impression that your wireless dongle is TrendNet (TEW-424UB).

If your using edgy (I hope you are for your sake), you can just install ndiswrapper from commandline (be sure to find a wired network to work from or you can download the necessary files from [http://packages.ubuntu.com/](http://packages.ubuntu.com/))
```
sudo aptitude install ndiswrapper
```
if your using dapper, you'll need to compile it from the source code (I'll help you do this if it is the case).

Then using either your windows install or your driver cd, you'll need to find a file called sis163u.inf (I think).  Save the file in your home directory

In the terminal do this
```
sudo ndiswrapper -i sis163u.inf
sudo ndiswrapper -l

```
At this point you should see something telling you that your wireless hardware exists.  If so get excited!

then
[codesudo ]depmod -a
sudo modprobe ndiswrapper[/code]

You should then be able to use your wireless card.  To make sure you can, in the terminal type
```
iwlist scan
```
which should give you a list of wireless networks.  If it does, congrats, you have a working wireless card...

finally in the terminal type 
```
gksudo gedit /etc/modules
```
and make sure that ndiswrapper is in the list.

Hopefully you'll have a working wireless card everytime you boot!

Be sure to post about what didn't work and/or didn't make sense or was just plain wrong.  If it did work, congrats and let us know!

Source: [http://ubuntuforums.org/showthread.php?t=105820](http://ubuntuforums.org/showthread.php?t=105820)

---

### Post by spankymasterc on 2007-04-04
i am talking to him and i will help em setup the wirless hopefully

---

### Post by river_plate_2005 on 2007-04-04
hey, thnks for the help but i still cant configure my wireless and yes iam using TEW 424UB and ubuntu 6.10.
My first question is how do i install ndiswrapper? 
waht i did was ..i put in the ubuntu cd then it said if i wanted to open package manager or something like that to install software. So i went yes and i found ndiswrapper  in the list but there were 4 of them so i marked all 4 and clicked apply. So it installed and stuff, then i went to terminal and typed:
sudo ndiswrapper -i sis163u.inf
but it said invalid driver!...
which inf do i need as i got the software from the trendnet website and under the driver folder there is windows 98, xp, me, 2000... and they all have that inf file.
thnaks a lot

---

### Post by kevinlyfellow on 2007-04-04
> **river_plate_2005 said:**
> hey, thnks for the help but i still cant configure my wireless and yes iam using TEW 424UB and ubuntu 6.10.
My first question is how do i install ndiswrapper? 
waht i did was ..i put in the ubuntu cd then it said if i wanted to open package manager or something like that to install software. So i went yes and i found ndiswrapper  in the list but there were 4 of them so i marked all 4 and clicked apply. So it installed and stuff, then i went to terminal and typed:
sudo ndiswrapper -i sis163u.inf
but it said invalid driver!...
which inf do i need as i got the software from the trendnet website and under the driver folder there is windows 98, xp, me, 2000... and they all have that inf file.
thnaks a lot

There are two versions of ndiswrapper, 1.8 branch and 1.1 branch, you installed both.  I'm not sure which ndiswrapper you tried installing with, so, to be sure you can instead try this

```
sudo ndiswrapper-1.8 -i sis163u.inf
```

Hopefully this works, but I installed both versions and mine defaulted to 1.8.  Oh, and you should use the WinXP driver.  I know other's have got their wireless working with the dongle, so you should be able to also

---

### Post by spankymasterc on 2007-04-04
Setup your tew424ub from trendnet
ok so here we go lol

Step1. Open terminial ( applications > accessories > terminal )

Step2. Type cd Desktop (notice the case Desktop not desktop)

Step3. Type or copy and paste  svn co [https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper/](https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper/) ((click on this link first and copy the url because it doesnt show all of it on forums ))

Step4. If you look at your desktop you now have a folder named ndiswrapper, now do this 

You can copy and paste them in terminal and if the first two commands give you errors its fine......

> sudo rmmod ndiswrapper

sudo ndiswrapper -e sis163u

cd ndiswrapper

sudo make uninstall # might try running that twice

make

sudo make install

you have it installed now. next plug in your trendnet thingy if it isn't already, and set it up. for example:

> sudo ndiswrapper -i /path/to/sis163u.inf
sudo modprobe ndiswrapper

hardware is up and working now.

> iwlist wlan0 scan This should give you a name for example your Essid the name of your network

> sudo iwconfig wlan0 essid YourEssid (<---- the name of your network)

sudo dhclient3 wlan0 #to do dhcp else, use ifconfig wlan0.

you should be set. 
Good luck and i see you got your dual boot up and running hooray for me lol j/k if u need help hit me up on msn :D

---

### Post by river_plate_2005 on 2007-04-04
cool thks..i will go check that...

everytime i tried installing the inf it didnt work but i finally got that working....

i have dual boot and my windows doesnt recognize my ubuntu...but in ubuntu my c: is listed as hd1.
i searched my hd1 for inf files and found sis163u.inf in there so i typed:

sudo ndiswrapper -i /media/hd1/windows/system32/usbdevice/sis163u.inf

then i typed:

sudo ndiswrapper -l
and it showed my driver present and hardware exist...

then i typed:

sudo depmod -a

then i typed:

sudo modprobe ndiswrapper 
it sais module not present????

whats wrong cant any one help plz?/

---

