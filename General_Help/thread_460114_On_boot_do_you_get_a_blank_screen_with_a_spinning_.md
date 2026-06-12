---
title: "On boot do you get a blank screen with a spinning busy Icon? This may help!On boot do"
date: 2007-05-31
forum: General Help
---

### Post by cosbear on 2007-05-31
On boot do you get a blank screen with a spinning busy Icon? This may help!
 

 I had been trying to reconfigure my login in login window under the system/administration menu and among other things had turned off AutoLogin, when I rebooted I got a blank screen with the busy icon in the middle of it.  I couldn't find any mouse moves or keystrokes which would get me out of there.  I had to use the power button to shut down and reboot.  Here is a synopsis of how I solved the problem with the help of a new forum buddy.  Shout out to benmoreassynt.  He knew just how to get me back into the system:
 

 I booted the machine and in the boot startup sequence posts when I saw the Grub notice I hit the Esc key,  
 (you have a 3 sec window).  It brought up a menu, and I used the down arrow key to highlight menu entry:
 

 [COLOR=SeaGreen]Ubuntu, kernal 2.6.20-16- generic ( recover mode )[/COLOR]
 

 That brought up;
 

 [COLOR=SeaGreen]root@(your computers name):~#[/COLOR]
 

 I typed in:
 

 [COLOR=Red]startx[/COLOR]
 

 and hit enter to start an xwindow so I could graphically reach the Opperating System and figure out how to solve my problem.  (I am still a neophyte when it comes to the command line interface so I needed to get to Graphical User Interface.  Blush!)  It opened a root window and had an error message on it that said:
 

 [COLOR=SeaGreen]Internal Error failed to initialize HAL![/COLOR]
 

 Since the last thing I did before my problem started was to alter the login in the login window under the System/Administration menu, I went back there to see if setting  automatic login back to on for cosbear would get me back in, but I got an error message which said something like this: [COLOR=SeaGreen]gdm not started[/COLOR].  GDM is gnome display manager, so I went to places/computer and chose file system and then opened the etc directory.  There was a directory called gdm in there so I opened it and found a file called gdm.conf, a configuration file.  I right clicked and chose the popup menu entry= [COLOR=SeaGreen]open with file editor[/COLOR].  In the file I found these lines:
 

 [COLOR=SeaGreen][ daemon]
# Automatic login, if true the first local screen will be logged in
# as user as set with automatic key.
AutomaticLoginEnable=false
AutomaticLogin=[/COLOR]
 
I saved the file before editing in case I needed it later, to the same directory named gdmBAD.conf and then I changed the last two lines to:

[COLOR=SeaGreen]AutomaticLoginEnable=true
AutomaticLogin=cosbear   [COLOR=Black](you would use your user name here)[/COLOR]
[/COLOR]
 

 So then I saved it back to the gdm directory with the original file name gdm.conf.  Now I hoped when I rebooted it would autologin right to my desktop and my problem would be solved.  So I went to the system menu and chose Quit.  Because I was in a xwindow instead of a gdm window it brought up a menu with only these choices:
 

 [COLOR=SeaGreen]logout – lock screen – switch user[/COLOR]
 

 I chose logout which brought me back to a command line prompt.  So I typed in:
 

 [COLOR=Red]exit[/COLOR]
 

 and pressed enter and it gave back:
 

 [COLOR=SeaGreen]init: rcs- sulogin main process (4656) terminated with status 1[/COLOR]
 

 so I figured it was safe to use the power button to shut down (depending on your machine you may have to hold down the power button for several seconds until it shuts the machine down) and then restarted, it booted up and automatically logged me in and took me right to my desktop ( A lovely sight I must say ).  Everything was right as rain so I guess that was the whole problem.   
 

 I can't guarantee this will solve your problem, but it might.  Good Luck
 

 If this doesn't work for you, you might want to check out these threads for some good information that may help lead you to a solution:
 

 [http://ubuntuforums.org/showthread.php?p=2752934#post2752934](http://ubuntuforums.org/showthread.php?p=2752934#post2752934)
 

 [http://ubuntuforums.org/showthread.php?t=459174](http://ubuntuforums.org/showthread.php?t=459174)
 

  This tip comes with no promises and no support, It worked for me on Ubuntu feisty fawn 32bit: Ubuntu, kernal 2.6.20-16, use it at your own risk.  Remembear that if you edit any scripts like the gdm.conf file please be sure to save an original copy first in case you need it later.  If you have any problems or questions feel free to send me a personal message and I will try to help if I can.
 

 FREESOURCE  a chance to breathe freely again, so exhale..........

---

