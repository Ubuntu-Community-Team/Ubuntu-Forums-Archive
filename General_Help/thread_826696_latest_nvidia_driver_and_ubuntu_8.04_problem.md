---
title: "latest nvidia driver and ubuntu 8.04 problem"
date: 2008-06-12
forum: General Help
---

### Post by smrh4004 on 2008-06-12
hello to all, to start with I am a new to Linux and don't know a signal command

so I go the wubi and installed ubuntu 8.04 beside winxp i boot into it and everything worked then I tried to use the fancy visual effects, so I went to appearance and clicked on visual tab and then the normal effect, I was told that I need the latest nvidia driver, I clicked OK and it automatically downloaded and installed the driver, upto this point I was very impressed with ubuntu and Linux and wondered why didn't I tried it sooner.

I was told to restart, and then the login screen came, put in the user name and then password and after that the screen just remained the colour of log in screen and nothing else was in the screen and nothing else happened, I could see the mouse and after few clicks a grey box appeared and nothing else.

Today I installed kubuntu instead, once I loged into it, I was told I need the latest nvidia driver which was automatically download and installed and after restart everything WORKED, but I just realised that ubuntu comes with mush better stuff, and I would like to have ubuntu instead of kubuntu.

any ideas?

---

### Post by trevelyan on 2008-06-12
you can install the Gnome GUI by typing the following in a terminal:
```
sudo apt-get install ubuntu-desktop
```
and press enter.

then log out and from the login screen change your session to Gnome.

---

### Post by smrh4004 on 2008-06-12
how do bring up the terminal for typing the code, the log in screen is the only thing that comes up, after i put in my user name and password i just end up with a screen with nothing in it

---

### Post by Enroth on 2008-06-12
Not sure if I am answering the question you are asking, but you run that command in KDE (kubuntu) from your post you seemed to indicate that you could still log into it.
To get the terminal up you go to the Kmenu and the (sorry a bit rusty from here on) applications and then terminal (like i said a bit rusty, so you may have to look for it through several other options) it will  either be labeled terminal or Konsole/Console, or even command prompt.

If you cant get into KDE you will have to wait for someone more experienced I'm sorry.

---

### Post by smrh4004 on 2008-06-12
Sorry for confusing stuff,

Ok when i installed ubuntu and after nvidia update driver (because i was trying to enable visual effects), i restarted the computer and after log in screen nothing happened, just a blank screen with the brownish colour that ubuntu uses. there was nothing in the screen and but i could see the mouse

then i removed ubuntu all together and installed kubuntu, and the driver was again updated automatically but i managed to get past the log in screen and things worked.

now i want to uninstall kubuntu and go back to ubuntu, but i still have this problem with nvidia driver update in ubuntu

the graphic driver gets updated and after restart and log in screen nothing happens.

i hope this is a bit clearer

---

### Post by Enroth on 2008-06-12
Clearer yes (but I may still be a bit confused, mainly because I am only just returning to Linux after a while)

The command given to you up the top "sudo apt-get ubuntu-deskto" will install the gnome (or what you got with your original install, so basicaly what you want) but it will also leave installed KDE (kubuntu).

If you have already done this and it is just gnome not working (but kde is) I have no idea. I also have not come across the auto driver installer (i just installed a driver for a 9800, as in between my first post here and my second) but didnt get the option for an auto install.
Not sure what card you have, but the guide I used was found here
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)
and at first glance it seems to have worked very well (although probably not what you want right now, if you are able to fix your problem up, but still not able to get the driver to work this should help)
* if you look over this and decide to try it to fix your problem (I wouldnt recomend it) you will probably have to change the last comand
"sudo /etc/init.d/gdm start"
to
"sudo /etc/init.d/kdm start"
Like I said though I wouldn't recomend it (but only because I dont know enough about both your problem and everything these instructions do, take anyone elses word over mine :p)

---

### Post by trevelyan on 2008-06-12
ok smrh4004... now im confused... is your KDE desktop working? (the only diference between Kubuntu and Ubuntu is that one uses KDE desktop envirioment and the other one uses the Gnome desktop envirioment)
so.. if your Kubuntu is working.. do it from there.. enter to your kubuntu and look for the Konsole, which is what the terminal is called in Kubuntu. i dont know exactly where it is becuase i only use Gnome.

anyways.. after the instalation... log out.. and in the login screen youll see a button or something that reads sessions. click it.. and change your session to Gnome. this is actually having both Kubuntu and Ubuntu in the same instalation. all you do is pick which one you wanna use. again.. no real difference between the two. exept for KDE and Gnome.

anyways.. if you have Ubuntu installed... (that is, you installed it from scratch)
have you tried to download the proprietary drivers from nvidia.com? try that and see how it goes. ofcourse.. do it before updating the drivers automatically.

i hope you have a better idea of what to do now.

---

### Post by smrh4004 on 2008-06-12
@Enroth
i have removed kubuntu and installed the ubuntu from scrach, then i followed the instructions in [http://ubuntuforums.org/showpost.php...71&postcount=6](http://ubuntuforums.org/showpost.php...71&postcount=6)
i was given the chance to select the graphic card in step 11, i selected the fx series from the menu after starting the gdm the resulotion stayed at 800 by 600, after restarting the computer i got the same problem, after the log in screen i just ended up with a screen with a brownish colour with nothing in it!

@trevelyan
if i start kubuntu from ubuntu, will i get all the applications that come with ubuntu, like firefox?

---

### Post by Enroth on 2008-06-13
OK I will try and answer the question directed at trevelyan first.
Keep in mind this is a hard thing for all new users to grasp but when you do understand.

**Ubuntu**: Ubuntu is what most people start with, it is the generic name for the Operating System talked about here on this forum. It is shipped with one of several Display managers.

**Gnome**: A Display Manager 
**KDE**: like Gnome it is a Display Manager 

**Display Manager**: This is the tricky bit to explain. As far as the end user (you) goes there are large differences, it will define how you interact with the desktop itself, how you navigate around the system, and where the "start" menu is. But as far as the computer is concerned it makes little difference, the underlying commands are all the same, as is the file structure. _This means that yes you can run all the same applications in one, the same as the other, on top of that if you install it in one it will already be installed in the second_

Kubuntu is shipped with KDE and Ubuntu is shipped with Gnome.

Now as for the question you have asked me Im sorry but Im out of ideas, but I can tell you how to get more people (and most better qualified than me) to help. At the moment this thread is in the General help, if you make a new thread (or if its possible move this one (never tried it)) in the 'Hardware & Laptops' section you should get a number of people looking at your post that can help. If you do post make sure you include the following things.
the version you are running (Hardy Heron)
your graphics Card make and model, (the exact model is best but if not that at least the series)
and as much detail of the problem as possible, maybe include a link to this thread as well.

Apart from that good luck in fixing this problem, I know it can be disheartening to do the same thing over and over (when I first tried Ubuntu I had graphic card problems as well), but keep at it once you have it set up and working Ubutnu is a really nice OS to use.

P.S. after reading though my own comment I realize I may sound a bit demeaning, not my intention (also not always that clear but like I said I find it hard to explain)

---

### Post by smrh4004 on 2008-06-13
thanks for all the help, i did try it in hardware and laptop section the same day i made this thread and here is the link for the other thread

[http://ubuntuforums.org/showthread.php?t=826678&highlight=latest+nvidia](http://ubuntuforums.org/showthread.php?t=826678&highlight=latest+nvidia)

i haven't tried envy yet, i have un-installed and installed ubuntu so many times now, i am very disappointed, it is difficult to get to know a os when you cant even get past the log in screen.

thanks anyway, i think i would give up,

p.s. just to round things off, the graphic card is nVIDIA GeForce FX Go5700

---

### Post by trevelyan on 2008-06-13
did you try
```
sudo apt-get install ubuntu-desktop
```
from the Konsole in Kubuntu?

since you've been installing and unistalling its hard to keep up with your current setting. so since you say Kubuntu worked, do this:

install Kubuntu
install the driver
run the Konsole (i think its in Kmenu > system > Konsole)
type: sudo apt-get install ubuntu-desktop
type your login password if asked.

after all files have been downloaded and installed, log out.
click the "sessions" link in the login window
select "Gnome" from the list
after you put in your username and password, you will be asked if you wanna make this the default desktop manager (or something like that) or if you wanna use it just for this session. you decide.


maybe like this it will work.

also, something you have to understand is that you can use any KDE application in Gnome and vise versa. so you dont really need gnome to run a gnome app or the other way around.

hope this helps.. and DONT GIVE UP. i reinstalled my ubuntu like 11 times before i could solve a diver issue with my graphics card. but once you know how to do it, its easy. :popcorn:

---

### Post by smrh4004 on 2008-06-14
hello again, read what 

*Marius Gedminas  wrote on 2007-01-17:  (permalink)*

wrote in

[https://bugs.launchpad.net/ubuntu/+bug/49594](https://bugs.launchpad.net/ubuntu/+bug/49594)

he says

[I]This happens to me often:
1. I boot the machine, log in
2. after some time I press Ctrl+Alt+Backspace to log out quickly
3. I get a gdm login screen and log in again
4. I get a blank desktop and nothing happens.[/I]

the symptom is same for me, although i am not sure about the log out or log in, i think it happens to me because i try to install the nvidia driver, i have tried all the solutions in that bug report, like killing bono... and natulius, but apparently they are not running anyway, this one guy says

[I]I think I had this bug before with an earlier version of Ubuntu. What had caused it was that I had taken out the lines
auto lo
iface lo inet loopback
from my /etc/network/interfaces file. Adding those lines back in fixed the problem for me. Hope this helps.[/I]

now i had to modify interfaces file to

[B]auto eth1

iface eth1 inet dhcp
wireless-essid Do not even try 
wireless-key 4d****************[/B]

otherwise the wireless will not work for me, i tried the GUI interface and all other network interfaces but this is the only way for wireless.

so you see, there could be many things responsible for this and i do so many different things every time, there is no way of keeping track and no guarantee with kubuntu once i install the ubuntu-desktop, i have installed and removed ubuntu ***56*** times now!

i am impressed with Linux, for a free software it delivers a lot but i think it still has a very very long way to go when compared with windows, and no i don't hate MS, all these problems have made me respect MS even more.

apologies to all Linux, Mac or other OS lovers!

p.s. i might try fedora 9 using Unetbootin, but i wonder how easy it will be, i couldn't sort out the ubuntu problem and ubuntu was meant for people like me (people that have never used linux before)

---

### Post by trevelyan on 2008-06-14
wow.. sorry man.. i was just trying to help. :S

i've been using linux for about three weeks. i never used anything other than windows before.. and yes.. windows is easy to use. im not using linux becuase im sick of windows. i simply like the control it gives me over my computer... i, like you.. during the first week couldnt to get it to work the way i wanted. i fixed one thing for another one to give me problems.. i was thinking.. windows is better. this doesnt happen to me in windows.. window this windows that... then i realised... this is not windows.

you see.. i was pretty good using windows.. and that doesnt count when using linux. its hard for a lot of people to go back to being biggeners. but thats what you and me are right now. so the best thing is, forget about windows when youre using linux. they are not the same. get that in your head.

linux is for whoever wants to use it. that doesnt mean its for everyone.

but now.. putting all that aside...

what do you mean "no garantee with kubuntu once i install ubuntu-desktop"?
do you mean by that that the driver will not work in kubuntu and ubuntu both? and can you tell me if you have actually gone to the nvidia website and downloaded the linux driver from there?

EDIT:
also.. concider dualbooting with windows if you dont already. thats what i do. that way if there is something wrong with linux or you dont wanna bother with it right now.. you use windows. gives you time to cool off :D

---

### Post by trevelyan on 2008-06-14
i just went to the Nvidia website and for the latest linux driver, your card IS supported.
look at the supported products list at:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

give that driver a try if you havent already. :)

---

### Post by smrh4004 on 2008-06-14
hmm, ok lets not compare,

i have tried the "run" file from nvidia website, and also envyNG, still no joy, i am starting to think that this whole thing is bug rather than a graphic driver issue. i am going to give it a one more try tonight, i wont install the driver or change anything, just restart the computer a couple of times to see what happens

the driver worked in kubuntu, by "no garantee with kubuntu once i install ubuntu-desktop"? i mean, what if i install ubuntu on top of kubuntu, if all my problems are because of bug in ubuntu then the final result will be the same

also, i am dual booting with windows xp, some time back i was thinking of doing a triple boot between winxp, fedora 9 and hackintosh Leopard, just for the fun of it!!!!!!

i saw this on a clip in youtube, check it out

[http://www.youtube.com/watch?v=dj-K-RwMOTA](http://www.youtube.com/watch?v=dj-K-RwMOTA)

---

### Post by trevelyan on 2008-06-14
hey.. i say give it a try.. install ubuntu-desktop in Kubuntu.
this isnt getting rid of kubuntu... its simply having both.. ubuntu and Kubuntu in one install.

i think.. if its a ubuntu issue... when you try using Gnome it wont work.. but guess what... you can still pick KDE instead, and it will work..

and if you wanna get rid of Gnome.. just do
```
sudo apt-get remove ubuntu-desktop
```

also.. another thing... i curently have a problem with my graphics driver..
the problem is that its not compatible with kernel verions higher than 2.6.24.16 so i always boot using 2.6.24.16 kernel from the boot menu.. so maybe.. its something like that on your end.. but i dont know for sure. im not aware of an incompatibility like that with the nvida driver. but it doesnt hurt to boot from an older kernel to see if things work.

EDIT:
that video looks very interesting... :D

---

