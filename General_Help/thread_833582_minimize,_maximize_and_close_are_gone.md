---
title: "minimize, maximize and close are gone"
date: 2008-06-18
forum: General Help
---

### Post by HappyFeet on 2008-06-18
when i open any app, the the min, max, and close buttons on the top right are now gone. i can right click the top bar and do these things, but is not ideal. any ideas to get these back?

---

### Post by RonB123123 on 2008-06-18
Could you please post a screen shot of one of the windows without the buttons?

In case you do not know, to post a screenshot, just hit the "Print Screen" button. It's normally located above the arrow keys, near the top of your keyboard.

---

### Post by HappyFeet on 2008-06-18
here you go

---

### Post by Habbit on 2008-06-18
If that is Xubuntu/XFCE, you can go to the XFCE Control Panel (or however it is named) and recover them in the "Window Manager" options. If that's Ubuntu or Kubuntu, I'm lost - try switching the theme.

---

### Post by HappyFeet on 2008-06-18
changing the theme doesnt do anything. btw, it's gnome.

---

### Post by Habbit on 2008-06-18
This [page]("http://asktheadmin.wordpress.com/2008/05/01/ubuntu-quick-tip-missing-minimize-and-maximize-window-buttons/") seems to describe your very problem. If you don't want to read through it, it seems that you should reinitialize the Metacity window manager:
```
metacity --replace
```

---

### Post by HappyFeet on 2008-06-18
thanks for the link, but it's still a no go.

---

### Post by Therion on 2008-06-18
I get this a lot.  I assume you're running Compiz?

The easy thing to try first is the F11 key, hit it twice.  If still no joy, ```
 compiz --replace & gtk-window-decorator --replace &
```

---

### Post by HappyFeet on 2008-06-18
no, im not running any effects. i didnt even install the nvidia driver.

---

### Post by Therion on 2008-06-18
Did you try running the command anyway?  I believe Compiz is running as the default window manager, regardless of you turning on any fancy effects or not.

---

### Post by HappyFeet on 2008-06-18
hitting F11 gives me full screen and suddenly the buttons appear. but disappear when the window goes back to normal size. no joy.

---

### Post by HappyFeet on 2008-06-18
this is what i get after running the command:
```
don@shadow:~$ compiz --replace & gtk-window-decorator --replace &
[1] 6153
Checking for Xgl: not present. 
[2] 6154
don@shadow:~$ No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


```

---

### Post by Therion on 2008-06-18
Arrrrrghhh...```
gnome-window-decorator --replace
```
Report back with joy, please.

Just saw you're running metacity, (sorry, I'm slow tonight) and the```
metacity --replace
```
line didn't do the trick for you, you say??  Odd... 

Not sure what else to tell you at the moment.

---

### Post by Habbit on 2008-06-18
Hmm... this may sound as reminiscent of an obsolete operating system but... have you tried rebooting? Or at least exiting your session and logging in again.

---

### Post by HappyFeet on 2008-06-18
yes, i have rebooted and even got all the system updates. ive tried all suggestions so far with no luck.

---

### Post by mc4man on 2008-06-18
In the vein of throwing stuff against the wall maybe try not changing a theme but pick customize -> window border and try switching to something else
or reinstalling ubuntu-desktop and metacity

---

### Post by djringjr on 2008-11-22
I am having the same problem, if I run
```
metacity --replace
``` everything is ok.

I also had the terminal just appear all white - and unmovable.

When I run metacity --replace I can access the terminal.

I had to run terminator to run the command :-)

Can anyone tell me how I can make the ```
metacity --replace
``` permanant?

When I log-out I loose the minimize, resize and close buttons and terminal is all white again.  Also when this is acting up, when I run "synaptic" - all I see is the window for password - but it is all white and not movable.  If I run metacity --replace and don't close the terminator, I get the password entry window.

Anyone got a fix or work around?

David

---

### Post by djringjr on 2008-11-22
I should mention that if I run :
```
metacity --replace
```
everything is ok, but the terminal never reverts to a prompt.  If I kill the terminal, the minimize, maximize and close buttons are gone, and if I start a program like terminal (but NOT terminator), Synaptic, I get a white unmovable screen with no text.  I can tell with Synaptic that it is the "enter password" screen - but there is no area to submit the password, and no "close window" button.

Right now I am just running the code above and letting it run.  If I reboot I have the same problem - but this is an annoying work-around.

Anyone got any any advice?

Thanks 

David

---

### Post by m_duck on 2008-11-22
Press alt + F2 and type ```
gconf-editor
```Then navigate to "Apps -> Metacity -> General". In the right hand pane there should be an option called "button_layout". If the value for this is empty, this hopefully explains the problem. The original contents of it would be:
```
menu:minimize,maximize,close
```

---

### Post by djringjr on 2008-11-22
The settings as are you show, but it does not work.

Thank you,

D

---

### Post by mrterry on 2008-11-29
Hi all

I had this problem with ubuntu + compiz where the window minimize/maximize close buttons disappeared. Several hours and several google searches later I finally found the problem.

Go to the compiz configurator (Advanced Desktop Effects Settings). Locate "Window decoration" and edit settings.

Locate "Decoration windows" and "Shadow windows".

For me those fields were empty. Set them both to "any", and your missing window buttons will (hopefully) appear again!

Hope this helps someone :)

---

### Post by djringjr on 2008-11-29
It seems to be a bigger problem than that - I haven't tried your fix yet though.  This also results in invisible missing text in the pull down menus.

It can be fixed by running ```
metacity --replace
``` in a terminal.  The command never cycles through like I'd expect it to, but continues executing in a loop - but as long as it is kept running everything works ok.

Some of the programs that have problems until this command is used are gftp opera - and of course the general problem with all of the programs having no corner minimize, full screen and close buttons.

It must be a gtk problem - perhaps one package that is installed by a user adds a problem to the standard Ubuntu.

I've made two threads on this - and not gotten the attention of anyone who could fix this yet.

I do get various gtk errors like this one:

Gtk-CRITICAL **: gtk_text_layout_get_iter_location: assertion `GTK_IS_TEXT_LAYOUT (layout)' failed at /usr/share/perl5/Video/DVDRip/Logger.pm line 109.

I'm trying to see if I can edit a home video that I put on dvd.  I have to convert it to avi or other format first.  :-)

Be well,

DR

---

### Post by kodman1113 on 2008-11-29
the minimize, maximize and close keys have done that to me before I'm not exactly sure how to stop this from happening but it might happen when a search is redirected.

---

### Post by djringjr on 2008-11-29
This seems to be a GTK error - I know how to work around it - execute that metacity --replace command - but I'm trying to alert someone to this bug.

Best
DR

---

### Post by mike2357 on 2008-11-29
There are some issues involving older Nvidia drivers and compiz.  I suggest trying  System -> Preferences -> Appearance -> Visual Effects (tab), and select None.  Does that make a difference?

---

### Post by djringjr on 2008-11-29
I am indeed using an older Nvidia driver - but sadly I already found that tab and it is checked.  We're getting warmer I think!

Thanks,

DR

---

### Post by Wartender on 2008-11-29
Dr, this may be a crude solution, but if metacity --replace works and you don't want the terminal window open you can go to system->preferences->sessions and click add and put metacity --replace in the command and it should run fine if you reboot (or log out and then in again i guess) of course this is not a solution to the main question but it should work for you, if you don't want to reboot do that and then open a terminal and type "metacity --replace &" and you can close it.

---

### Post by djringjr on 2008-11-29
Thank you, Wartender.  That extra & does allow me to closer terminal!

I should mention that probably changing the effects setting as previously mentioned fixed the upper right hand side of the window "minimize, full screen toggle, and close buttons" but the problem with invisible drop dowm menu text persists until I issue the ```
metacity --replace &
``` command.

After this command, gFTP, Opera and the other programs with invisible text - which I am now absolutely sure are missing because of a GTK bug, are visible.

Thanks ever so much Wartender!

Best

DR

---

### Post by bezo on 2008-11-30
Hello, Ubuntu users,

I met the same problem with these buttons and I looked many forums for help.
I'm a very new user of LINUX based programs, so I don't know if me example could solve your problem too.

At first these buttons disapeared when I tried to solve problem with my CRT monitor resolution and refresh rate at the starting of UBUNTU.

I found this website where was description how to solve this problem editing xorg.conf file (look at the **problem 3**):
[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

I followed all steps, and after restart all problems with minimize, maximize and close buttons began. After many tries to solve new bug, I looked back to file xorg.conf 
I decided to take original xorg.conf file, make only **4-6 steps** (with my own monitor resolutions) and save these changes.
After that I just restarted PC and looked what happens when I change VISUAL EFFECTS from NONE to NORMAL and EXTRA.
And I was surprised, that everything was OK.
So at this moment everything is perfect with these buttons and I can't see no new bugs :)

here is my xorg.conf from inside:

Section "Monitor"
	Identifier	"Configured Monitor"
 	HorizSync	30-71
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection      "Display"
        Depth           24
        Modes           "1152x864_75"
        EndSubSection
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


**My PC:**
CELERON 1200 Mhz
Seagate 40 GB
Samsung 80 GB
NVIDIA GeForce 2 MX/MX 400
UBUNTU 8.10

---

### Post by kodman1113 on 2008-12-08
Try clicking the F11 key. it will might get rid of it.:-k

---

### Post by sameerds on 2008-12-17
Found the same bug reported in Gentoo:
[http://bugs.gentoo.org/show_bug.cgi?id=241860](http://bugs.gentoo.org/show_bug.cgi?id=241860)

Apparently it is fixed by upgrading libmetacity0 to version 2.24. The default installed in Intrepid is 2.22, while 2.24 is available in updates.

I just tried doing that because I was facing the same problem in Compiz. And now it works. What I can guess from the discussion on the Gentoo bug is that gtk-window-decorator is responsible for drawing those buttons, and it depends on libmetacity ... even if you are using Compiz.

---

### Post by farhado on 2008-12-22
> **Habbit said:**
> This [page]("http://asktheadmin.wordpress.com/2008/05/01/ubuntu-quick-tip-missing-minimize-and-maximize-window-buttons/") seems to describe your very problem. If you don't want to read through it, it seems that you should reinitialize the Metacity window manager:
```
metacity --replace
```

The command solved my same problem instantly, Cheers

I had tweaked the window manager in order to speed up my boot time. The moral is evident I guess!

---

### Post by newbie02 on 2009-01-04
ok this worked for me also....
Note I was also having issues with blank terminal windows. This solution also fixed that problem.

I did the following
1. Press alt + F2 and type 'sudo metacity --replace' then click run.
2. I see min,max and close return :). Terminal window now works. 
   Thank you very very much.

Part 3 is where I need help for now this is how I implemented the solution. If you know of a better way please explain why its better then what im currently doing.

3. go to System->sessions
   a)click add 
    b) name it then add line 'sudo metacity --replace' (dont use ' just what is between)


Thanks again
newbie02

---

### Post by marianlibrarian on 2009-07-23
I am experienceing this with Kubuntu 8.04.2 KDE. Not only are all windows missing these buttons, but also when I open any window, (example a browser window or a setup window or a word processor window) it is like it is glued to the center of the screen. If I open another window, I cannot get to the window underneath because it is covered. I have to close the top window. I cannot move or resize any windows either.

Is there a command that works in Kubuntu KDE to "reset" this? 

I have two users set up. The patron user settings are still the same. But my admin user is the one messed up. Otherwise I would just delete the low privileged user and start all over. 

I have been trying to figure this out for several hours and this thread was the closest I have seen to my problem.

Thank you in advance.

---

### Post by djringjr on 2009-07-23
marianlibrarian

Use Update Manager to update your installation to the latest Ubuntu - the issues are all fixed.

You can also do this in a terminal:

```
update-manager -d
```

David

---

### Post by marianlibrarian on 2009-07-23
Thank you.

I am about to go into a meeting. I will do this first thing in the morning and let you know how it worked. :)

---

### Post by marianlibrarian on 2009-07-24
update-manager -d did not work

the termanal window says "command not found"

?

---

### Post by marianlibrarian on 2009-07-24
WAIT!!!

Edit:
Just in case you start piddling around with KDE like I did because it is new and different:
Beware:
There are several different places to adjust how your screen looks, how your menues look and a bunch of other things.

My mistake fixed:
Go to System - Desktop effects - 1st reinstall compisengine and THEN select No effects

Now I am back in business. The last time I did that I don't know why but I uninstalled something called compizengine and that made a mess for me.

Hope this helps someone else sometime.Kubuntu, 8.04.2 KDE

---

### Post by djringjr on 2009-07-24
@marianlibrarian

update-manager -d

Should work!  It does on my computer.  You'll also find it under System / Administration.

Be well,

DR

---

