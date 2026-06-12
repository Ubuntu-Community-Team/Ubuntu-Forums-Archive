---
title: "Compiz fault again LT 16.04"
date: 2018-07-29
forum: General Help
---

### Post by harfin on 2018-07-29
[SIZE=3]I have had to post my situation before, most recently to thread I started in May, [https://ubuntuforums.org/member.php?u=886503](https://ubuntuforums.org/member.php?u=886503)

After being returned to some degree of normality post May 2018 my laptop was until 3 days ago working OK 

As before on earlier hassles along the same lines, compiz is modified during a software update, and my toolbars (top and side) are nowhere to be seen.

In earlier times I was able to re-boot to an earlier update by clicking exit during the booting exercise

This time I get no choice to revert to an earlier version. 

The message during a 'normal' boot, that I get is *"Ubuntu has experienced an internal error"* to which I select the send a report option.

Of course, this time I have no option to reboot using a previous version, but I do now have a document saved to my desktop (which I can see) which includes a hyperlink to this forum, which I can invoke by highlight the link and control/click it.

It seems there is no fix for this hassle, so I have ordered a CD/DVD of 18.04 which should be with me in a couple of days.

Please can anyone offer any suggestion for a quick reprieve until the new version arrives? I assume that someone will take action with the report I logged, and issue an update solving (at least until someone updates compiz again.


HELP!
Alan


[/SIZE]

---

### Post by mc4man on 2018-07-29
post results of 

```
cat .config/compiz-1/compizconfig/config 
```

---

### Post by harfin on 2018-07-29
The result of that is 
> [general_ubuntu]profile = unity-lowgfx


---

### Post by harfin on 2018-07-29
[SIZE=3]On reopening the terminal the following has appeared as well:
[HTML]No command 'profile' found, did you mean: Command 'profiles' from package 'samba' (main)
profile: command not found[/HTML]

I have to open a new terminal session each time, as my browser is fixed in the foreground, and I am unable to revert to the desktop without closing the browser first[/SIZE]

---

### Post by #&amp;thj^% on 2018-07-29
Try this again in a terminal:
```

export DISPLAY=:0   
dconf reset -f /org/compiz/
```

and then
```

setsid unity

```

---

### Post by harfin on 2018-07-29
harfin@harfin-HP-255-G1-Notebook-PC:~$ export DISPLAY=:0   
harfin@harfin-HP-255-G1-Notebook-PC:~$ dconf reset -f /org/compiz/
harfin@harfin-HP-255-G1-Notebook-PC:~$ setsid unity
harfin@harfin-HP-255-G1-Notebook-PC:~$ compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity-lowgfx


(process:4183): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range
Switched to profile 'unity' (for environment 'ubuntu')
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compizconfig - Error: Unable to find interface type 3 on 0x12795b0 
This is either a programmer error or more than one static library 
defining this interface has been linked in
Unable to continue, please file a bug about this
unity-panel-service stop/waiting
unity-panel-service start/running, process 4221
start: Job failed to start

---

### Post by #&amp;thj^% on 2018-07-29
Reboot

---

### Post by harfin on 2018-07-29
[SIZE=3]
Sorry to say, that has made no difference.

I cannot, just like before those changes, access my toolbars (top or side).

I have a screen which is icons of things saved to my desktop.

The mouse permits me to open / access any of the items saved in my desktop, but nothing else in terms of access to parts of my system, to alternative locations or access to programmes. The only exception to that is that a right mouse click does enable me to open the terminal and the like.

I will attempt shortly to see if I am able to reboot to an earlier system, just in case that option is available.

Thanks for your input; really appreciated.

Harfin

[/SIZE]

---

### Post by #&amp;thj^% on 2018-07-29
Yep this is really broken the only other thing to try here is:
```
mv ~/.config ~/.config_backup
```
This will reset everything and your Ubuntu system will resemble the looks of a fresh install. Installed applications will be untouched.
Sometimes a simple log-out and back in again works but I would suggest another reboot to be sure.
Fingers Crossed.

---

### Post by dragonfly41 on 2018-07-29
Just a thought ...  installing Gnome Flashback might give you the reprieve you are looking for?

[https://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/](https://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/)

---

### Post by harfin on 2018-07-29
[SIZE=3]Well if nothing else all that activity seems to have _enabled_ me to at least boot with the previous headers update (.130 rather than the latest headers from 3 days ago which ended in .131)

I can by booting with that set of headers I have access to my toolbars, and at a first look at now will enable me to switch to 18.04 LT.

I hopefully will have the disc in a day or so, and I imagine that will enable me to have a total new Ubuntu installation, not an update of the 16.04. Is that so? I haven't had to do that before.

Other than the DVD for 18.04 is there anything else I need to do as a pre-load precaution (other than my normal full back up of all files, settings etc.?

Thanks for all your help.

Regards

Alan aka Harfin

PS Is it a good idea to try the "[/SIZE][COLOR=#000000][FONT=&quot][SIZE=3]mv ~/.config ~/.config_backup" and should I also[/SIZE] "[/FONT][/COLOR][SIZE=3][COLOR=#000000] ... install Gnome Flashback? [/COLOR][https://www.debugpoint.com/2016/04/i...placing-unity/]("https://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/")[/SIZE][COLOR=#000000][FONT=&quot]

[/FONT][/COLOR][SIZE=3]
[/SIZE][SIZE=3]
[/SIZE]

---

### Post by #&amp;thj^% on 2018-07-29
> **harfin said:**
> [SIZE=3]is there anything else I need to do as a pre-load precaution (other than my normal full back up of all files, settings etc.?

Thanks for all your help.

Regards

Alan aka Harfin


[/SIZE]
If you are using any 3rd party PPA's remove those and fully update the system again.
But if you are referring to clean install just backup what you need>>>be careful with your old settings using them in 18.04 might give you more problems.
Things are a lot different with 18.04 from 16.04.
I wish you much success with your new install though. :)

> PS Is it a good idea to try the "mv ~/.config ~/.config_backup" and should I also " ... install Gnome Flashback? [https://www.debugpoint.com/2016/04/i...placing-unity/](https://www.debugpoint.com/2016/04/i...placing-unity/)

It won't hurt anything to try either one.

---

### Post by harfin on 2018-07-29
[SIZE=3]Alas I should not have tempted fate and advised you that all was well. Subsequent re-boots using the header set ending in .130 _did not_ work again :-(

I am currently restricted to using my hyperlink to the forum page that I had embedded in a document saved to my desktop.

I will now endeavour to use that [/SIZE]mv ~/.config ~/.config_backup option

[SIZE=3]


[/SIZE]

---

### Post by harfin on 2018-07-29
[SIZE=2]I now have a simple toolbar, but (hopefully) it will enable me to operate for the few days until I get set up with 18.04.

Thanks again for all your help!

Alan[/SIZE]

---

### Post by #&amp;thj^% on 2018-07-29
It wouldn't hurt to check that you logged into Ubuntu and not the Flash-back session.

---

### Post by harfin on 2018-07-29
I only tried the "[COLOR=#000000]mv ~/.config ~/.config_backup option".

I've have now rebooted three times after that first successful attempt and I am presented with the sames short simple menu that I referred to above!

All is well. :-)




[/COLOR]

---

### Post by mc4man on 2018-07-29
Regarding unity, you are getting the lowgfx  profile which is a degraded experience.
Maybe your hardware isn't up to snuff or maybe the setting is erroneous. I'd edit that file (.config/compiz-1/compizconfig/config) to this & reboot and see what happens (- if you're still using unity..
```
[general_ubuntu]
profile = unity
plugin_list_autosort = true
```
After editing go 
```
mv .cache .cache.bak && reboot
```

---

### Post by harfin on 2018-07-30
[SIZE=2]At least this menu enables me to use the laptop until the 18.04 LTS disk arrives on Wednesday.

I am somewhat hesitant to attempt to modify the situation again at this point in  time in case I end up having yet another "no access" period!

Thanks for your advice and assistance; it's greatly appreciated.

Harfin[/SIZE]

---

