---
title: "Ok... I am seriously Frustrated and have done this ..."
date: 2008-06-16
forum: General Help
---

### Post by Grimm310420 on 2008-06-16
I have done this sevral times using wubi deleting and trying again and again  using wubi... and a ISO image CD that i made of the OS of being able to do it in windows and its really making me mad because I know my system should be able to work with linux... On the download everything goes fine as it should be its just when i get to this boot menu this is what happenens.  my model is a HP Pavillion a1310n  and the system specs are. This is the problem i am getting at the start menu...  now whe ni go to the wubi loader i choose 32 bit edition and unbuntu...
 
[http://youtube.com/watch?v=GOh5YYP9dd0](http://youtube.com/watch?v=GOh5YYP9dd0)     (Copy And PAste into Browser)



-system specs:

Proccessor: AMD 3700+ @ 2.2GHZ single core 
Memory: (2) 512mb DDR Ram
Hard Drive: 200 Gigs...
onboard video...

---

### Post by pytheas22 on 2008-06-16
Do you know what kind of video card you have?  If you're not sure, boot to Ubuntu, and when you get to the login screen, press control-alt-f2.  You will be brought to a command prompt.  Log in on that and type the command:

lspci

You'll get a list of all your hardware.  Look for the line relevant to your video card--it probably says something like "VGA controller: ..."  Copy down that line and please post it here.

Also, are you able to log in if you select Gnome Failsafe Session or Failsafe Terminal?  You can try this by clicking the "Select Session" button at the bottom-left of the login screen.

---

### Post by Grimm310420 on 2008-06-16
Yea it has intergrated graphics within the Mobo of the comp ATI Xpress 200 series... is there a problem with this?

---

### Post by |{urse on 2008-06-16
that card works on ubuntu, though not fantastically. Still it should work with the ati driver or the vesa at the very least. edit : now that i watch your youtube video.. what model monitor is that? Just for diagnostic's sake try hooking up a different monitor if you have another one handy and try it again.

---

### Post by Grimm310420 on 2008-06-17
Ok... I currently dont have another monitor but its been a good monitor for over the past two years... its just a two year old HP Vs15 monitor....

---

### Post by Captain_Riker on 2008-06-17
Just a suggestion: After pressing ctrl+alt+f2 (or from grub choose rescue) copy down your x11.conf. For starters have a look at the logs in /var/log/(messages,dmesg,daemon.log . . .). Seems your X-Server crashes.

---

### Post by pytheas22 on 2008-06-17
This looks like quite the same problem as the original poster's: [https://answers.launchpad.net/ubuntu/+question/26538](https://answers.launchpad.net/ubuntu/+question/26538) .

You might want first to try getting the proprietary ATI driver installed and see if the problem goes away.  I've never dealt with ATI cards myself, but from what I hear, the simplest way of getting them set up is to use envy.  You can install it by pressing control-alt-f2 to get to a command line, and typing:
```

sudo apt-get install envyng
```

then run the command-line interface with:
```

sudo envyng -t
```

and follow the simple instructions, then reboot.  If this doesn't solve your login problem altogether, I think it will at least move you closer to a solution.

Also, it would be helpful if you logged at the logs for X to see what it's complaining about when it crashes.  At the command-line, you could type:

```
cat /var/log/Xorg.0.log | less
```

and scroll through it to see if there's any problem mentioned.  The log is convoluted and I can't tell you exactly what to look for, but anything about being "unable" to do something or "restarting X" or anything else along those lines is what you want to look for.

---

### Post by Grimm310420 on 2008-06-17
ok where do I find propitiery drivers?

---

### Post by ago on 2008-06-18
May I suggest the video forum? 

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334) 

As this is not strictly a wubi issue and you should get better support there.

---

### Post by pytheas22 on 2008-06-18
> ok where do I find propitiery drivers?

To get the proprietary drivers, just follow my instructions in the post above regarding envy.  Once you install envy it will automatically fetch and install the appropriate drivers for you.

---

### Post by ago on 2008-06-18
Make also sure you install all the updates

---

### Post by Grimm310420 on 2008-06-19
ok thanks... I kind of understand half of what your saying I do no under stand lol

---

### Post by Grimm310420 on 2008-06-19
the only thing i am confused about is after I enter the first code what is the command line interface?

---

### Post by pytheas22 on 2008-06-19
> the only thing i am confused about is after I enter the first code what is the command line interface?

I'm not sure what you mean...this is what you need to do:

1. press control-alt-f2 to get a command line and log in.  Then type:
```

sudo envyng -t
```

2. this will open a text-based interface that looks like this:

       +-----------------------------------------------------------+
       |    EnvyNG Menu ver.1.1.1                                  |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Restart the Xserver                                |
       |                                                           |
       |    7 - Restart your computer                              |
       |                                                           |
       |    8 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+

3. type "3" and press enter to tell the program to download and install the ATI driver.  It should do everything for you automagically, as they say.

4. reboot and see if you have better luck logging in

---

### Post by Grimm310420 on 2008-06-19
OK.. I did what your other post exactly word for word on what to do and this is what came up. about downloading envy... I pressed ctrl-alt-f2 got in to the command console... typed in this command: Sudo apt-get install envyng... and this is what shows up now keep in mind this is the first code that u told me to type. After typing and hitting enter this is what it says.

Reading Packagelists...Done
Building Dependency Tree
Reading State information... Done 
E: couldnt find package envyng



that what it looks like when I type that first command in. an afterward it just goes to if u wanna type another command again... I tried also typing that second command but it did not recognize the command at all.


Is this something that I did? Or am I missing something?

---

### Post by pytheas22 on 2008-06-19
Sorry, I might have given you bad information.  I thought that all of the repositories are enabled by default in Hardy but I might be wrong; I don't remember.  In any case do this to make sure you've got everything enabled:

After logging in on the command line:
```

sudo -s
echo 'deb http://archive.canonical.com/ubuntu hardy partner' > /etc/apt/sources.list
echo 'deb-src http://archive.canonical.com/ubuntu hardy partner' >> /etc/apt/sources.list
echo 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse' >> /etc/apt/sources.list
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse' >> /etc/apt/sources.list
echo 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse' >> /etc/apt/sources.list
apt-get update
```

then try:
```

sudo apt-get install envyng
```

again and it should work.

---

### Post by Grimm310420 on 2008-06-19
type all that?

---

### Post by dlmoak on 2008-06-19
Enter one line at a time and hit Enter after each line.  You should copy and paste the text to avoid errors.

---

### Post by pytheas22 on 2008-06-19
> type all that?

Yeah, unfortunately it's the only way I know how to do this from the command-line (if anyone else knows better please elaborate).  If you could log in graphically it would be much easier, but the commands above are the only way to do this by hand.

Another workaround that might save you typing but might not work, depending on whether the dependencies for the envyng package are satisfied, is this:
```

wget http://mirrors.cat.pdx.edu/ubuntu/pool/universe/e/envyng-core/envyng-core_1.1.1ubuntu11_all.deb
sudo dpkg --install envyng*
```

but again I don't know whether this will work or not.

---

### Post by Grimm310420 on 2008-06-19
wait can i copy and paste it to the command center?

---

### Post by pytheas22 on 2008-06-19
Also it's just occurred to me that if your graphics card is external (i.e. PCI or AGP) and you also have an onboard graphics adapter, it might be easier to temporarily unplug the external card and fall back to the onboard one.  That way you'd at least be able to log in to Gnome (assuming that your failure to do so now is the result of your graphics card, which I think it is), where you could copy and paste commands and use the GUIs.  If you want to try this approach, unplug your external card, hook up your monitor the onboard one and try logging in.  If it still fails, you probably need to run this command:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

and then you should be able to log in.

---

### Post by Grimm310420 on 2008-06-19
now i am confused... this is comp is using onboard video... no graphics card...  so what do I do?


 I need to know how to get my linux to work using onboard ATI video...??? which commands do i use?

---

### Post by Grimm310420 on 2008-06-19
ok using my onboard video which is the only thing that i have on this comp i am able to log into linux with the failsafe gnome session what do i do while in here ... just tell me what to do so I can finally get this thing to work maybe u could post Screenshot of where to go maybe? i dunno i just know that i can login in the gnome session.

---

### Post by Grimm310420 on 2008-06-19
OK... ignore those last few posts I got it to work but now when i log into linux for somereason the  linux is cut off by the screen for some reason and I dont know how to fix it.

---

### Post by pytheas22 on 2008-06-19
The onboard/external card suggestion was just to make things easier on you if you had two video cards--I didn't know whether you did or not--but you can ignore all that since you don't.

So you're able to log in to a normal Gnome session now?  What did you do (I guess you logged into the failsafe session and used envy)?
> 
when i log into linux for somereason the linux is cut off by the screen for some reason and I dont know how to fix it. 

Do you mean that part of your screen is not visible?  Could you provide a screen shot please or describe in greater detail?

---

### Post by Grimm310420 on 2008-06-19
ok i fiexed everything and it worked for about 4-5 now i just logged in and it goes to white screen and stays there... and it was working perfectly what do i do?

---

### Post by Grimm310420 on 2008-06-19
I can still acess the fail safe mode but when i go into system buy in go into the admin section now... and i go back to hardware drivers... and now it say "No Propiteary drivers in use." does this mean anything to anyone?

---

### Post by pytheas22 on 2008-06-19
> ok i fiexed everything and it worked for about 4-5 now i just logged in and it goes to white screen and stays there... and it was working perfectly what do i do?

Sometimes desktop effects can cause it to do things like this, especially if the computer has been hibernated or suspended.  To see if it's desktop effects, press alt-f2 and type "metacity --replace" (you won't see anything, but just type that and press enter).  If the screen comes back, then you know it's desktop effects and we can try to solve it.

If you used envy and it ran successfully, then you have the proprietary driver installed.  The hardware driveras thing sometimes screws up and gives bad information, so it could just be that.  I would try running envy again and see what happens after that.

So try the metacity --replace command and running envy again and report back, please.

---

### Post by Grimm310420 on 2008-06-19
Do I login @ first? cause i did and when it went to white screen i pred alt-f2 and typed "metacity --replace" exactly how you had it and nothing happened.i had to manual shut down.

---

### Post by pytheas22 on 2008-06-19
Yes, you are supposed to do the the alt+f2 thing after logging in.  So I guess desktop effects aren't the problem.  Can you log in normally after you reboot the computer?  And what if you run envy again (did you run it in the first place or did you get things working some other way)?

---

### Post by Grimm310420 on 2008-06-19
i couldent get envy to run or didnt try to at least cause i was confused.... so i went into failsafe gnome mode and then once logged in I went to system- Administration- then hardware driver and it regocnized my onboard video and it had an option to enable it an i enabled it an now it doesnt show up at all.

---

### Post by pytheas22 on 2008-06-19
As I said earlier, the hardware drivers utility can be buggy.  If I were you, I'd do this:

log in to failsafe Gnome, and go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, check all of the boxes, then click close.  You'll be asked if the sources list should be updated; click yes.  This is going to do the same thing as all of those long commands that I typed out earlier today.

Then try to install envy again by opening a terminal (Applications>Accessories) and typing:
```

sudo apt-get install envyng-gtk
```

Alternatively, if you don't want to use the command line, open Synaptic Package Manager (under System>Administration) and search for envyng-gtk to install the package using a GUI.

Then run envy by typing:
```

sudo envyng-gtk
```

(this will start envy in graphical mode instead of text-based mode, which I assume you prefer; if not, you can still run it with a text interface using "envyng -t") and tell it to install the driver.

There are still other ways to troubleshoot the problem, but I think that the envy approach is going to be the simplest right now.

---

### Post by Grimm310420 on 2008-06-19
OK.... once again now i have gotten this to work now the last thing that i need help with with installing wine i followed all the instructions from this link... [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)  and followed all instructions but then i get this error... after trying to load. 


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



What does this mean i really wanna be able to play some FPS games on here...

---

### Post by Dutch70 on 2008-06-20
Run this in Terminal...
```
sudo dpkg --configure -a
```

and then install wine from "synaptic package manager" it's already there! Just tic the box beside it,  mark it and apply.

Congrats! Now you have Wine.  

Dutch

---

### Post by Grimm310420 on 2008-06-20
ok I understand the first part of what you are saying copy and pasting thatt code into a termianl but what exactly do you go for next? I have no idea what you are talking about in that 2 step i dont see that program... btw im new to linux only 3 days LOL

---

### Post by pytheas22 on 2008-06-20
Synaptic is a program to install/uninstall software.  You can access it under the System>Administration menu, or press alt-f2 and type "gksudo synaptic"  After you run the dpkg reconfigure command mentioned above, just start Synaptic and search for wine to install it.  Or you could always install from the command line with "sudo apt-get install wine."

---

### Post by Grimm310420 on 2008-06-20
thank you.

---

### Post by Grimm310420 on 2008-06-20
lol ok now is there any type of software on linux to where I can make movies? if so please tell me how or where to get it.

---

### Post by pytheas22 on 2008-06-20
I'm not sure exactly what kind of movies you want to make, but if you mean how can you edit and produce video on Linux:

Kino is a nice and simple basic video editor.  Cinelerra is a very powerful editor, but you're going to have to do some reading first to learn to use it.  I've also heard that Blender is good, but I've never used it myself.  For burning to DVD check out tovid or dvdstyler.

Everything mentioned above is available by default in Synaptic, with the exception of Cinelerra, for which you have to enable an additional repository first; see the directions at [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu) .

---

