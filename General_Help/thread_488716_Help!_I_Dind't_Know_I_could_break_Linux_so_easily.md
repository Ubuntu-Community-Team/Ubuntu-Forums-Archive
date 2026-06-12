---
title: "Help! I Dind't Know I could break Linux so easily"
date: 2007-06-30
forum: General Help
---

### Post by Nimaran on 2007-06-30
I am new to Linux, but I have liked what I have seen. However, I managed to install Beryl and I don't know if this is related to this or not, but when I was shutting my computer down for the night, it was being weird so I hit ctrl + alt + esc and a bunch of text flashed up, I wasn't able to see what it said, then it shut down normally. I booted in the next morning and logged in and my desktop gradient blue came up with my mouse pointer, but nothing else and it just stays like that. I can move my mouse and stuff, but I have to ctrl + alt + backspace in order to leave. I didn't know the computer could shut down wrong and break the whole thing. Please help. I don't want to have to abandon Linux.

P.S.- I had restarted the computer with Beryl without a problem, the only other things I had installed I think was a mp3 codec, and a package to help get my wireless working, but I'm pretty sure I had restarted since then, so I don't know if those effect this.

P.P.S.- I have posted this elsewhere on this forum, but we got nowhere any ideas here would be great.

P.P.P.P.S- System Specs:

Dell Dimension 2400
Pentium 4
Dual Boot with XP
Nvidia Geforce fx5200

Pleasse Hellppp!!!

---

### Post by m.musashi on 2007-06-30
What is crtl-alt-esc supposed to do? I'm not familar with that.

So, lets see if I understand. You can boot and log in but your desktop is just blue with a mouse and nothing else? Can you right click and get any kind of menu? Can you lauch any apps? You might want to boot the safe mode and see what happens. This is pretty odd and I'm not entirely sure how to fix it. How important is it to get this working? If you won't lose anything important, it might be worth doing a reinstall. When I was new I broke everything a lot and reinstalled a lot. It might be possible to fix this (might be really easy). It just depends on how anxious you are to get going again or what you want to recover.

If you can boot the recover mode. see if the dmesg command prints anything that looks like errors. I'd say post it, but i'm not sure how you would do that without a desktop and access to firefox (typing it by hand would be a pain).

---

### Post by Nimaran on 2007-06-30
ctrl + alt + esc brings up the skull and crossbones, which I then clicked on the blue, no I can't right click either. I am not sure how to launch apps without being able to acess anything (not trying to be sarcastic. I don't know if you can do it via CLI)

Yeah, I guess I could do a reinstall, but I was only temporarily able to get a phys. connection to the internet, and I downloaded a lot of stuff I needed or wanted. (e.g. beryl, mp3 codec, media organizer, open office) and unless I can get my wireless working without internet after the reinstall. I would be in a cookie, if this isn't one. I am not familiar with CLI and when I boot into recovery I get the command line is their a way  to access the gui from there? Any help would be greatly appreciated. Thanks.

---

### Post by raashell on 2007-06-30
So, if you'll scroll down to page 2 (at the moment) you'll see that I had a similar problem.  What I'm about to say is sort of lame, but I hope it helps.  

 I was logging into ubuntu and nothing would start- I'd get a beige background screen with mouse pointer and then after a few seconds a blank white square would pop up in the upper left half of the screen.  Then- nothing.

So what I did eventually, was leave to get something to eat and came back in five minutes.  The desktop loaded up.  :P   I have no idea why it took so long or what the error was, but it's working now... So wait longer- give it a shot.

---

### Post by Nimaran on 2007-06-30
hah, thats funny I'll try give me a couple minutes I'll boot in and see.

---

### Post by eggdeng on 2007-06-30
> when I boot into recovery I get the command line is their a way to access the gui from there
```
startx
```

---

### Post by m.musashi on 2007-06-30
> **Nimaran said:**
> ctrl + alt + esc brings up the skull and crossbones, which I then clicked on the blue, no I can't right click either. I am not sure how to launch apps without being able to acess anything (not trying to be sarcastic. I don't know if you can do it via CLI)

Yeah, I guess I could do a reinstall, but I was only temporarily able to get a phys. connection to the internet, and I downloaded a lot of stuff I needed or wanted. (e.g. beryl, mp3 codec, media organizer, open office) and unless I can get my wireless working without internet after the reinstall. I would be in a cookie, if this isn't one. I am not familiar with CLI and when I boot into recovery I get the command line is their a way  to access the gui from there? Any help would be greatly appreciated. Thanks.

I wonder it that's a beryl feature. ctrl-alt-esc doesn't do anything for me. However, for you it sounds like it launched xkill. Clicking the desktop might kill nautilus or something but a reboot should restore that. Right clicking on the desktop should open a menu with a few options - one of which allows you to create a launcher. We could have used that to launch some apps.

If you can boot recovery, try running a few commands to fix anything broken
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get check
sudo apt-get clean
sudo dpkg --configure -a
```

See if that causes anything to install.

You can start your gui desktop from the terminal by doing
```
startx
```
Do that after the update and such.

During the recovery boot while all the text is flying by do you see anything odd like errors? I know it's hard to catch but dmesg should show those too.

Did you make any changes to any config files? If you installed beryl, you probably made changes to /etc/X11/xorg.conf. From the terminal mode type
```
sudo nano /etc/X11/xorg.conf
```
and undo those changes. Or you can restore from a backup if you made one.

That's about all I can think of right now.

---

### Post by Nimaran on 2007-06-30
I just discovered something. Yipee! I was waiting like you said, and then just on fluke I hit the key commands to rotate desktops and they rotated to the beryl icon that is on the top and bottom which means its not broken, maybe it is just taking a long time to load. In a little bit I'll give it more time and see what it does. Does that change any of your ideas, because it is all still there, but not really... THnaks again

---

### Post by m.musashi on 2007-06-30
Sounds like you have beryl autoloading. I'd remove that option and see if things load normally. You can remove it by booting recovery and then
```
ls /home/your_username/.config/autostart
rm /home/your_username/.config/autostart/whatever.desktop
```

---

### Post by Nimaran on 2007-06-30
So, will that get it out of my auto load, and boot xfce normally?

---

### Post by raashell on 2007-06-30
Nimaran,

  Again, don't know if this will help, but I eventually found out my problem was caused by altering my /etc/network/interface file, using instructions pulled off the web, in an attempt to make my virtual windows machine network with my host Ubuntu.  I had saved a back up copy and when I replaced it and rebooted everything loaded okay again.  Good luck!

---

### Post by m.musashi on 2007-06-30
Oh, you are using xubuntu? It should be the same but i'm not totally sure. But, yes, if you remove the auto load option beryl will not load and if beryl is the cause of the problem (and it sounds like it is) then everything should load normally. Let us know and if it doesn't we can go from there.

---

### Post by Nimaran on 2007-06-30
I tried that and I'm going to post the output as in image file ;)

It didn't work, but I think I probably did something wrong.

Ok, cant post image its on my computer, give me your email and I'll send it to you, no span or anything promise. :)

---

### Post by tater_3001 on 2007-06-30
this happend to me when i tried to get compiz fusion... what i did is hit alt+f2 ... the box doesnt show but it is up... type "metacity --replace" without the quotes... you wont be able to see what is being typed... and hit enter... thats what fixed it for me

---

### Post by m.musashi on 2007-07-01
> **Nimaran said:**
> I tried that and I'm going to post the output as in image file ;)

It didn't work, but I think I probably did something wrong.

Ok, cant post image its on my computer, give me your email and I'll send it to you, no span or anything promise. :)

Check my lauchpad page for an email address. I'd rather not post it in a forum.

[https://launchpad.net/~jimhutchinson/](https://launchpad.net/~jimhutchinson/)

---

### Post by Nimaran on 2007-07-01
I managed to boot into Xubuntu recovery mode and access the graphical interface. I went to the startup directory and removed beryl manager loader from there, but beryl still starts up when I load it normally. Well, not really load, everything is still blue and all I can do is rotate the screen, but I discovered I can bring the terminal up. I think were getting closer I can smell it, and I really do appreciate all of your guys help.

---

### Post by steveneddy on 2007-07-01
> **Nimaran said:**
> ctrl + alt + esc brings up the skull and crossbones ... .

lol

That's xkill - you killed the gnome manager.

Restart, hit Ctrl+Alt+F1, or try to get to a terminal log in.

Log in and type 

```
sudo /etc/init.d/gdm restart
```

To restart X, do a 

Ctrl+Alt+Backspace

---

### Post by Nimaran on 2007-07-01
YES!!! Not everything is broken. I have managed to load thunar and any other app by the alt + f2 command. So, I loaded bery l manager told it to go back to Xfce (got to it from usr/bin) then I went down and loaded all the Xfce sftuff I could.

Now even though it seems to be running, the computer doesn't recognize it. (e.g. when I try to log out is says Xfce isn't running and to log out by  a diffrnet way.)

Whenever I start a new session it goes back to the way it was.

When I try to switch back to Beryl all the title bars disappear.

My screen resolution is lower than I want it to be, and my normal (1024x768) dosen't appear in the options menu.


Any help on these remaining problems would be great. Thank you all.

---

### Post by Nimaran on 2007-07-01
Fixed resolution, forget that problem.

---

### Post by Nimaran on 2007-07-01
I have successfully fixed my computer. I would like to thank all who helped me get this done. I still am unsure however what will happen if I start a new session, but I'll cross that bridge when I come to it. Thank you all again. I felt like I had the globe helping try to fix this problem. ;)

---

### Post by sabrewolf2006 on 2007-07-01
Hi, 
I've been experiencing a similar problem too..
I have discovered its basically down to a confusing GNOME session configuration...

In my case I have installed both beryl and compizfusion... I saved my session settings in order to retain compiz on login rather than beryl but had left beryl-manager in the session startup.. (like a fool didn't realise that beryl-manager would remember for me, another reason to keep the Gem around :D )

The next time I logged in I got the plain blue screen but when I hit ctrl+alt+bkspce I can see my desktop is underneath.. once X had restarted and I logged back in, everything came up just fine...

So to sum up:
you need do is check your session manager to make sure you haven't got any dodgy configuration of compiz and beryl

System > Preferences > Sessions (in GNOME - not sure about xfce's session management)

Hope this helps

---

### Post by m.musashi on 2007-07-02
> **Nimaran said:**
> I have successfully fixed my computer. I would like to thank all who helped me get this done. I still am unsure however what will happen if I start a new session, but I'll cross that bridge when I come to it. Thank you all again. I felt like I had the globe helping try to fix this problem. ;)

Sorry, I kind of tuned out on you. Looks like you got it fixed though. Congrats. Do you think beryl was the main cause of your problems? It sounded that way to me but you'd be the expert on your own machine. Anyway, I've had lots of good luck with beryl but it's very beta software and can break a lot of things. Beryl and compiz recently rejoined and I think the result will be a lot better stability. The new version is called compiz-fusion. I'm not sure I'd try and install it on top of beryl but I'd at least look into it if you want to use something like this.

---

### Post by Nimaran on 2007-07-02
Yeah, I think Beryl was the problem, but it is working now. Just one question how can I get both it and emerald to start on dfult?

---

### Post by sabrewolf2006 on 2007-07-02
> **Nimaran said:**
> Yeah, I think Beryl was the problem, but it is working now. Just one question how can I get both it and emerald to start on dfult?

If you set its decorator under beryl-manager to emerald it will start emerald along with compiz everytime.. Another reason for keeping that gem around :D

---

