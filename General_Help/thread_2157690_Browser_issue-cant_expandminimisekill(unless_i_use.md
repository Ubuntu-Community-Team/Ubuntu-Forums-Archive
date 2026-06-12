---
title: "Browser issue-cant expand/minimise/kill(unless i use command)"
date: 2013-06-26
forum: General Help
---

### Post by rapattack1 on 2013-06-26
The browser issue started on a new session today. I think when i was on the desktop yesterday there was some applet that came up saying something about a script issue and did i want to stop it or continue. I have seen this sort of thing before so did either or both. Stop script or continue. I dont fully understand why this happens and its been quite a while since it happened. 
The size of the browser is now half of the desktop and i can drag it around but there is also no cross int he corner to close it. Oh and i can quite via the file menu but then when i rerun it that isnt there. I also tried to just reboot the machine(twice) and that didn't solve anything. The main browser is firefox but i though i would try and see what chrome does. It also opened to the size of half the desktop, can't see the cross in the corner to close it but exit is in the right menu/corner. Not sure what to do:confused:

---

### Post by dino99 on 2013-06-26
maybe you should start to tell us which ubuntu is used, and which DE is used (unity/gnome-shell/...)

seems like a compiz crash; into a terminal, run:

dconf reset -f /org/compiz/
unity --reset-icons

---

### Post by rapattack1 on 2013-06-26
```
dconf reset-F /org/compiz/unity --reset-icons
The program 'dconf' can be found in the following packages:
 * dconf
 * dconf-tools
Try: sudo apt-get install <selected package>

```Hi i dont' know that first question u are asking sorry.
I have never interacted with compiz as i have no idea what it is i am afraid.
Just noticed i cant copy/paste either. Oh no cross in the top corner of the terminal either

---

### Post by rapattack1 on 2013-06-27
Ubuntu just did an update of firefox and i still have the same issue

---

### Post by rapattack1 on 2013-06-27
Hi can anyone help? I dont know what compiz is even though i am aware it exists. I think it is a theme/destop whatever thing. Maybe xfce is the thing we should be dealing with. I still dont understand what these things are fully...so would appreciate some help. Am using a livedvd of another distro as sick of trying to surf the net or use most apps. I have to use 'kill' via some other thing i can't remember. Sorry super busy and i have short term memory

---

### Post by Bashing-om on 2013-06-27
rapattack1; Hi !

To set the stage, so help can be provided:
```
lsb_release -a ##tells us what version you are running;
uname -r ## tells us what kernel in that version you are running;
apt-cache policy ubuntu-desktop ## IF you are running ubuntu, what desk top you are running. else .

```

Then instructions can be provided to restore the desktop.

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-06-28
Hi is there some shorter command as i also cant copy/paste anything for some reason...thanks

---

### Post by Bashing-om on 2013-06-28
rapattack1; Hi !

The commands in and of themselves are short.... all after '##' are "comments" not to be entered along with the commands.

Copy and paste: try key combos - ctl+c to copy, ctl+v to paste
maybe highlite the text andf shift+insert to paste
or maybe highlite and middle mouse button to paste ??

[INDENT][INDENT]hth[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-06-28
OK the copy and paste thing is not straight forward but this is the first output
> lsb_release -a ##tells us what version you are running;
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

> apt-cache policy ubuntu-desktop
ubuntu-desktop:
  Installed: (none)
  Candidate: 1.267.1
  Version table:
     1.267.1 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
     1.267 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main i386 Packages


---

### Post by Bashing-om on 2013-06-28
rapattack1; Hey, Making progress !

Referring back to dino99's post #2; We now know what distribution and version you are using and what desktop you are not using..
still need to know the desk top environment; So ->
```
apt-cache policy xubuntu-desktop
apt-cache policy lbuntu-desktop
apt-cache policy thunar
apt-cache policy nautilus

```
Off the top of my head I do not know of a better way to identify the desk top we are trying to restore, others can advise better - to be sure -// Hit or miss will eventually identify it !

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-02
> carla@carla-desktop:~$ apt-cache policy xubuntu-desktop
xubuntu-desktop:
  Installed: (none)
  Candidate: 2.152
  Version table:
     2.152 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
carla@carla-desktop:~$ apt-cache policy lbuntu-desktop
N: Unable to locate package lbuntu-desktop
carla@carla-desktop:~$ apt-cache policy thunar
thunar:
  Installed: 1.2.3-3ubuntu2
  Candidate: 1.2.3-3ubuntu2
  Version table:
 *** 1.2.3-3ubuntu2 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status
carla@carla-desktop:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:3.4.2-0ubuntu8
  Candidate: 1:3.4.2-0ubuntu8
  Version table:
 *** 1:3.4.2-0ubuntu8 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.4.1-0ubuntu1 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

Oh thanks glad to know we are getting closer. Sorry been busy and havent had a chance to get online :)) appreciate the help

---

### Post by rapattack1 on 2013-07-04
Did i post the right info?

---

### Post by claracc on 2013-07-04
Referring ro what desktop you are using, you can see it, running the following command:
```
echo $DESKTOP_SESSION
```

---

### Post by rapattack1 on 2013-07-04
Ubuntustudio

---

### Post by Bashing-om on 2013-07-04
rapattack1; Hey ..

Still making progress ..
Ok, I am not at all familiar with Ubuntustudio... Think It is based on xfce environment...
I am looking about and I will return when I know more.

[INDENT][INDENT]I'll be Baaccckkk[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-06
Yes its XFCE. Thanks because i am really baffled. I did use XFCE before with anutha distro that sort of looked like the mac os....it was a painful os to install but great to use. I broke it tho twice and it was very problematic to install so had to dump it :0(
Noticed there is a Ubuntustudio section on this forum too. Might c if anyone else is having this problem.
Here is what the about tab says about xfce:
Xfce is a collection of programs that together provide a full-featured desktop environment. The following programs are part of the Xfce core:

Window Manager (xfwm4)
Handles the placement of windows on the screen.

Panel (xfce4-panel)
Program launchers, window buttons, applications menu, workspace switcher and more.

Desktop Manager (xfdesktop)
Sets the background color or image with optional application menu or icons for minimized applications or launchers, devices and folders.

File Manager  (thunar)
A modern file manager for the Unix/Linux desktop, aiming to be easy-to-use and fast.

Session Manager (xfce4-session)
Restores your session on startup and allows you to shutdown the computer from Xfce.

Setting System (xfce4-settings)
Configuration system to control various aspects of the desktop like appearance, display, keyboard and mouse settings.

Application Finder (xfce4-appfinder)
Shows the applications installed on your system in categories, so you can quickly find and launch them.

Utilities and Scripts (xfce-utils)
Startup scripts, run dialog and about dialog.

Settings Daemon (xfconf)
D-Bus-based configuration storage system.

Xfce is also a development platform providing several libraries, that help programmers create applications that fit in well with the desktop environment.

Xfce components are licensed under free or open source licences; GPL or BSDL for applications and LGPL or BSDL for libraries. Look at the documentation, the source code or the Xfce website ([http://www.xfce.org](http://www.xfce.org)) for more information.

Thank you for your interest in Xfce.

	- The Xfce Development Team

---

### Post by Bashing-om on 2013-07-06
rapattack1; Hey .

xfwm is the window manager:
Maybe the session cache got corrupted.
First try starting the panel from the text login TTY;
```
xfce4-panel &
```
Anyway, your panel settings are safe in ~/.config
You can also clear the session cache: logout, ctrl+alt+f2, login in the text console again and:
```
rm -rf .cache/sessions
```
then ctrl+alt+f7 and login again -> will create the files to default values.


All back to normal ?

[INDENT][INDENT]a step in the right direction[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-07
Woot woot i stumbled through and at first nothing was changed. Then i did a reboot and everything looks great and works again. Thanks sooooooo much wow i can use cinelerra again yay. It wasn't even running before. Wow thanks sooo much he he i am so happy:popcorn:

---

### Post by Bashing-om on 2013-07-07
rapattack1; Haw haw and more lol !

Glad ya up and running..
Remember where you got it from and come back often ... and as you are able.. make a contribution to others welfare.

[INDENT][INDENT]open source, we are all in this together 
[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-08
Yes i am a very happy Linux gal and i always pass on the linux love. Everytime i come across a used old laptop that i give away to people that cant afford a computer i install linux. So many people have never even used windows and i get to give them something better so hopefully they never use windows. Then they dont get corrupted lol.

---

### Post by rapattack1 on 2013-07-08
Oops bad news the fix didnt stick. 24 hours later i am back to the same problem. Will do the thing again and see what happens.
OK did it again and it works again. So it doesn't stay fixed. Is there a way to fix that?

---

### Post by Bashing-om on 2013-07-08
rapattack1;

Well.. will have to find what is breaking what and when.....
What command are you doing do restore the desk top ?...maybe that will direct our attention to what is getting broken.
And Let's look at how the desk top is being started:
terminal command:
```
cat ~/.xinitrc
```

[INDENT][INDENT]an adventure in the offing ?[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-09
I got no such file or directory to that command. OK i used ctrl + alt + f2 then rm -rf-panel .cache/sessions then ctrl + alt + f7...then i reboot as at first there is no change and a reboot changes everything

---

### Post by Bashing-om on 2013-07-09
rapattack1; Morning .

I have no access to 'studio thus presently do not know how the DM is started... but here is a thought about the Session.

Each time the DM is started it is started from configs files based on what was ... so let us reset the "saved" Sessions.

Get your desk top as you want it ... and then:
Save the session: Setting manager > Session and startup > Session > Save session

Restart the system to see effect.

[INDENT][INDENT] I recon so[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-10
Hi this session it stayed the same as the last and didnt go back to the bad one so something might be working right...thanks so much for all your help. Will do that save session thing and see what happens.

---

### Post by rapattack1 on 2013-07-11
Hmmmmm today its back to the problem...it obviously happens when the computer is off....damn. So does this mean i have to save the session every session?

---

### Post by Bashing-om on 2013-07-11
rapattack1; Yuk ..
In looking at this, I discovered I do not know enough at this time to advise further. But I can say this.
I made some changes on my "~/.bash_logout" file ...- in my process of learning- And to my dismay, that file gets overwritten.
Some function is bring called in your situation such that "saved sessions" is not behaving as expected or is not being called appropriately.

How about starting another thread, with this as a the theme in that new thread to gain visibility to those with greater knowledge - as this thread is marked "solved" will not be seen by others.

I will meet you in that new thread, and continue to prosecute this.

[INDENT][INDENT]sometimes I wonder, other times I just do not know[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-11
[ATTACH=CONFIG]244612[/ATTACH]
Could this be something that can be edited?

---

### Post by rapattack1 on 2013-07-11
OK cool will do that real quick now as bed time in Australia :0)

---

### Post by Bashing-om on 2013-07-11
rapattack1;

"xfce4-panel" config files I expect are in the directory " ~/.config/xfce4/panel", " /home/<user_name>/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml" , as well as others I am not aware of at this time.

[INDENT][INDENT]It be a learning experience
[/INDENT][/INDENT]

---

### Post by rapattack1 on 2013-07-13
So either of these two?
[ATTACH=CONFIG]244699[/ATTACH][ATTACH=CONFIG]244700[/ATTACH]

---

### Post by Bashing-om on 2013-07-13
rapattack1;
Presently I do not know which files write to the "saved sessions". I am doing my homework in an attempt to understand.

xfce4 is also new to me - just a few months - so I am feeling my way as I go ! My prodding on my system to learn, sometimes has unexpected results. Like when I fired my system up just now ... startup session started apps and I am sure I closed all out prior to shutting this system down last night !

Which means when I shut down next, I will have to set my environment up to how I want it to start, and save that session. Then I expect I will see the expected results. One must save that session and should re-start with that configuration. My homework is where why and how !

As an aside, yeah I find I really like xfce4 as the DE. Just takes a bit to understand what config file is related to what action.

[INDENT][INDENT]still learning after all these years[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-13
rapattack1; Hey ...
Continued crashes back to the the TTY !
A couple of restarts from "trying" to reset a few times .. and a reboot ... now looks good here ! ..
What I finally did was:
```
rm -r ~/.cache/sessions/
```
Set my desktop up as I wanted it.

```
Setting manager > Session and startup > Session > Save session
```
restart - all came back up as expected;  (yeahhh !)
reboot - all came back up as expected. **

So far so good .. looks to be solid.

If you continue to have problems,,, how bout we clear ALL the current setting, and start all over from default settings ...see what haps ?
Reset up your desktop and then save the settings ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rapattack on 2013-08-12
Sorry i havent been on for weeks. My situation is not solved. I didnt realise til not i had two usernames on ubuntuforums and now its a bit of a mess but this is me ok :0) I have been temporarily getting around the problem by using this when the session is broken:
ctrl + alt + f2
login then
rm -rf .cache/sessions
then ctrl + alt + f7
then reboot
.....
after that i am fine for maybe 3 sessions. Always breaks again and i have to repeat :0(

---

### Post by Bashing-om on 2013-08-12
rapattack; Let's try this:

From terminal TTY1 ->
1. Shut down the panel first,
```

xfce4-panel --quit

```
2. Kill the xfce4 configuration daemon, 
```

pkill xfconfd

```
3. First delete settings for the panel, 
```

rm -rf ~/.config/xfce4/panel

```
4. Clear out the settings for xfconfd, 
```

rm -rf ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

```
5. Restart the panel, 
```

run xfce4-panel

```
This will respawn xfconfd automatically. Note if you need or want to restart xfconfd manually know that on my installation it was in /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd which was outside of $PATH.
This clears it for the running session, regenerates the files, and sets up the default for future sessions.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

