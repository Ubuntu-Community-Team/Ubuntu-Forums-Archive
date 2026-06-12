---
title: "transfer lxde configuration to new users"
date: 2014-03-12
forum: General Help
---

### Post by Nopposan on 2014-03-12
Hello there.

I am using Lubuntu and I made some desktop changes to my oem account that I want to be permanent for all new users. I tried putting the contents of my home folder in /etc/skel but that apparently only took care of transferring the desktop icons. I want to have new users get the clock time in 12-hour format, a larger the task bar, and maybe the different wallpaper.

How can I do that?

Thanks.

---

### Post by CaptainMark on 2014-03-12
You got the /etc/skel bit correct, any files placed there will be used when constructing a new user, it's just finding the correct files for what you want to configure. Off hand I think LXDE keeps it config files in ~/.config/lxpanel 

You're on the right track wait long enough and someone will certainly tell you more about which files to use

---

### Post by Nopposan on 2014-03-14
Thanks. I'm on the lookout, Cap.

---

### Post by ankspo71 on 2014-03-15
Through trial and error I found out that /etc/skel doesn't work for me as it is supposed to, but the good news is the *ubuntu distributions all use packages called '*ubuntu-default-settings' instead. If /etc/skel still doesn't work you could edit the default config options for multiple users.

The lxpanel default config file that needs to be edited for all new users is located at:
/usr/share/lxpanel/profile/Lubuntu/panels/panel

You can find more default settings for Lubuntu by opening Synaptic Package Manager and searching for lubuntu-default-settings, then right click on it and click on properties, then look at the "installed files".

---

### Post by CaptainMark on 2014-03-16
What exactly was your trial and error? 
With all due respect you must be doing it incorrectly because I've been using the /etc/skel method for years, its a perfect way to customise the guest session from Ubuntu's login screen.

This is the method:
1. Create new temporary user
2. Login in as temp user and configure anything to your will (Desktop layout / panel layout / default browser / browser homescreen etc etc.)
3. Log out of temp user and log back in as yourself
4. Copy config files from temp users home directory directly to /etc/skel ( ~/.config ~/.local ~/.gconf etc etc.)
5. Delete temp user

Now anytime you either create a new user or log into a guest session you'll have a desktop just like the one you created for the temp user.

---

### Post by ankspo71 on 2014-03-16
Hi CaptainMark,

My trial and error spans back a few years actually, and today I have found out that using /etc/skel still doesn't work for me. I have been trying to use /etc/skel for quite a while on several computers. I can't recall if I have ever tried this on other distributions though. The result was always either 'some' settings carried over to the new user (simailar to the problem the original poster's problem), or no settings were carried over at all. Earlier today they weren't copied at all twice. It sometimes seem to work well for me in the past if I only copy a couple of settings into /etc/skel while troubleshooting, but it won't work if I try to copy the majority of settings and some user data (wallpapers etc) into it. Something about /etc/skel doesn't seem to work properly (at least on my end), or maybe it is something about the files I place in /etc/skel. In the past I've gone as far as changing permissions of the items placed in /etc/skel, and edited the configurations of 'adduser' and 'useradd', and tried running those commands in the terminal once or twice, but I had no real success then. Using /etc/skel in Remastersys was always unsuccessful back in the day too, and a handful of other users back then had similar problems.

My method of using /etc/skel is the same as yours, with the exception of creating a temporary user to create the new settings because I have always copied my own user's settings and data into /etc/skel.

Edit: It seems to be working well and consistently using users-admin, for now. I haven't done anything differently yet, other than rebooting to be able to remove previous temp users with users-admin, and then create more new temp users to test. I'm going to have to give up on troubleshooting my own problem with /etc/skel because now I can't recreate the problem and I've been at this for hours today.

---

### Post by Nopposan on 2014-03-18
Well, I assume the gtk tool for managing Users and Groups is users-admin. It behaves a bit oddly for me; it acts as if it's removing users but then when I log out or even reboot, there they are listed in my login screen choices. When I try userdel temporaryusr9 on the command line I get an error saying that the user is still logged in: this is AFTER deleting the user using the gtk app. What the? Anyway, that's just an aside for now. I might post it in another forum.

Presently, I've got almost all of my settings transferring to the new user. The only one that I can't seem to find is the desktop background. Anybody know where the config file for setting the default background is? Anybody? Buehler? I did take a look at the files installed by the lubuntu-defaults package, but there are quite a few of them. Could it be the line "window_manager=openbox-lubuntu" in the /etc/xdg/lxsession/Lubuntu/desktop.conf file? What if I change it to just say "window_manager=openbox"? Isn't it the window manager that holds the desktop background up?

P.S. I found out how to force logout of the user. [http://www.serverschool.com/server-security/how-to-kill-a-user-session-on-a-linux-server/](http://www.serverschool.com/server-security/how-to-kill-a-user-session-on-a-linux-server/) The command is pkill -9 -u username. After that, userdel username works.

Thanks.

---

### Post by vasa1 on 2014-03-18
> **Nopposan said:**
> ... The only one that I can't seem to find is the desktop background. Anybody know where the config file for setting the default background is? Anybody? Buehler? I did take a look at the files installed by the lubuntu-defaults package, but there are quite a few of them. Could it be the line "window_manager=openbox-lubuntu" in the /etc/xdg/lxsession/Lubuntu/desktop.conf file? What if I change it to just say "window_manager=openbox"? Isn't it the window manager that holds the desktop background up?

Thanks.
I'm not sure that Openbox has anything to do with the desktop background. I think you need to right-click on an empty space on your desktop and examine the options there.

---

### Post by Nopposan on 2014-03-18
Thanks for your response, Vasa1. I do know how to change the background for the desktop in an individual user's account. What I'm trying to do is to change the default background for all new users. I suppose an easy solution would be to just change the contents of the default backdrop by naming my new default backdrop with the same name as the default and then naming the original default something else, but that's a bit of an ugly hack, IMHO.

---

### Post by vasa1 on 2014-03-18
> **Nopposan said:**
> Thanks for your response, Vasa1. I do know how to change the background for the desktop in an individual user's account. What I'm trying to do is to change the default background for all new users. I suppose an easy solution would be to just change the contents of the default backdrop by naming my new default backdrop with the same name as the default and then naming the original default something else, but that's a bit of an ugly hack, IMHO.

My point was that looking at the window manager wouldn't help you. Anyway, have you looked at /etc/xdg/lxsession/Lubuntu/desktop.conf ?

```
file_manager/command=pcmanfm
file_manager/session=lubuntu
file_manager/extras=

desktop_manager/command=filemanager
desktop_manager/wallpaper= <<<<<<<<<<<<<<<<<<<<<<<<

polkit/command=lxpolkit

network_gui/command=nm-applet

audio_manager/command=alsamixer

```I have no wallpaper --- don't use any --- but what happens if you provide the full path to a wallpaper of your choice?

---

### Post by Nopposan on 2014-03-18
"desktop_manager/wallpaper= <<<<<<<<<<<<<<<<<<<<<<<<"

Yes, I looked at it (see my previous post where I mention it.) I don't have a line like that in my desktop.conf file. I think I may just do the dirty hack. It's most efficient and doesn't require changing configuration files; it seems there's more than one place that this configuration can be set, and I don't want to override the end user's custom configuration by putting a desktop spec in a file where they can't overwrite using the GUI.

---

