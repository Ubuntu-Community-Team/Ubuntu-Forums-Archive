---
title: "Desktop and Login Wallpapers"
date: 2016-05-18
forum: General Help
---

### Post by Abdul_Hakim on 2016-05-18
Hello everyone,

I was doing some tweaking of Ubuntu and I ran this command to disable the Guest session:

[COLOR=#333333][FONT=Ubuntu]```
echo allow-guest=false | sudo tee -a /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```

Now that I've done this, the login screen only shows the default wallpaper, rather than matching whatever I set my desktop wallpaper to. I've tried googling for this issue and I can't seem to find anything for this specific context. How do I make it so that the login screen will go back to matching my desktop wallpaper?[/FONT][/COLOR]

---

### Post by CantankRus on 2016-05-18
> **Abdul_Hakim said:**
> Hello everyone,

I was doing some tweaking of Ubuntu and I ran this command to disable the Guest session:

[COLOR=#333333][FONT=Ubuntu]echo allow-guest=false | sudo tee -a /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

Now that I've done this, the login screen only shows the default wallpaper, rather than matching whatever I set my desktop wallpaper to. I've tried googling for this issue and I can't seem to find anything for this specific context. How do I make it so that the login screen will go back to matching my desktop wallpaper?[/FONT][/COLOR]

Reverse what you did...
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```
...remove the "allow-guest=false" line and save.
You may have to install **gksu**.

---

### Post by Abdul_Hakim on 2016-05-18
> **CantankRus said:**
> Reverse what you did...
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```
...remove the "allow-guest=false" line and save.
You may have to install **gksu**.

Right but wouldn't that re-enable the Guest user? The goal was to have Guest disabled. But if this is what happens if Guest is disabled and there's no way around it then I guess I can put it back.


EDIT:

Tried that, but the issue is still happening. Guest account has returned, but the login screen still only shows the default wallpaper, rather than matching my Desktop wallpaper

---

### Post by CantankRus on 2016-05-18
> **Abdul_Hakim said:**
> Right but wouldn't that re-enable the Guest user? The goal was to have Guest disabled. But if this is what happens if Guest is disabled and there's no way around it then I guess I can put it back.


EDIT:

Tried that, but the issue is still happening. Guest account has returned, but the login screen still only shows the default wallpaper, rather than matching my Desktop wallpaper

It must be something else you have done then.
I edited **/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf** using the command from your first post.
Rebooted and guest account has gone and the greeter still displays each users wallpaper.

---

### Post by Abdul_Hakim on 2016-05-18
That first command was literally the only thing. Nothing else changed :/

I've found lots of threads on how to make the login and desktop wallpapers different, but I just want it to go back to the default behavior of matching each other

---

### Post by CantankRus on 2016-05-18
Try this.
```
gksudo gedit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```
If it is empty add 
```
[com.canonical.unity-greeter]
draw-user-backgrounds=true
```
Just add the second line if "[com.canonical.unity-greeter]" exists.
Save and close then run....
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by Abdul_Hakim on 2016-05-18
> **CantankRus said:**
> Try this.
```
gksudo gedit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```
If it is empty add 
```
[com.canonical.unity-greeter]
draw-user-backgrounds=true
```
Just add the second line if "[com.canonical.unity-greeter]" exists.
Save and close then run....
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

Just tried, nothing changed. That file didn't exist so it created an entirely new blank file. I've seen that file referenced on other threads but for some reason my system didn't seem to have it. 

I don't know if this is related, but I had recently installed Compiz, although I haven't actually changed anything with it yet. Could that have anything to do with it?

EDIT: Sorry not sure why that double-posted

---

### Post by CantankRus on 2016-05-18
> **Abdul_Hakim said:**
> Just tried, nothing changed. That file didn't exist so it created an entirely new blank file. I've seen that file referenced on other threads but for some reason my system didn't seem to have it. 

I don't know if this is related, but I had recently installed Compiz, although I haven't actually changed anything with it yet. Could that have anything to do with it?

EDIT: Sorry not sure why that double-posted
That file is not there by default. It's a file you can create to override the default behaviour of the .xml files in the same directory.

By compiz I'm assuming you mean compizconfig-settings-manager which doesn't change anything by just installing.

---

### Post by Abdul_Hakim on 2016-05-18
> **CantankRus said:**
> That file is not there by default. It's a file you can create to override the default behaviour of the .xml files in the same directory.

By compiz I'm assuming you mean compizconfig-settings-manager which doesn't change anything by just installing.

Yep that's the one.

I just found this:
[http://askubuntu.com/questions/379965/lightdm-unity-greeter-wallpaper-will-not-set](http://askubuntu.com/questions/379965/lightdm-unity-greeter-wallpaper-will-not-set)

So I'm going to try his list of commands there, except this part:

gsettings set com.canonical.unity-greeter draw-user-backgrounds 'true'
Will update with results

---

### Post by Abdul_Hakim on 2016-05-19
Sigh, didn't work either. Got this output:

```
lightdm@computer:/root$ gsettings set com.canonical.unity-greeter draw-user-backgrounds 'true'

(process:5040): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=97319cc79ac4f02b02af476c573abd2c --binary-syntax --close-stderr': Child process exited with code 1
```

I think I'm just gonna reinstall at this point lol

---

### Post by vasa1 on 2016-05-19
Hi, it would be nice if you post any terminal output within code tags :)

You can select the text you want and then click on the little # sign to have opening and closing code tags flank the text. Or you could just add them by typing them in! The # sign is visible when you start writing a new post. If you don't see the # sign, click on "Go Advanced" just below the posting area.

I've done it for you in one post.

---

### Post by CantankRus on 2016-05-19
I have used those commands before to change things at the greeter as the user "lightdm" and they still work here.
Just tested...
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sudo -i**
[sudo] password for glen: 
root@Xenial:~# xhost +SI:localuser:lightdm
localuser:lightdm being added to access control list
root@Xenial:~# su lightdm -s /bin/bash
[COLOR="#0000CD"]lightdm@Xenial:/root$[/COLOR] **gsettings get com.canonical.unity-greeter draw-user-backgrounds**
true
[COLOR="#0000CD"]lightdm@Xenial:/root$[/COLOR] **gsettings reset com.canonical.unity-greeter draw-user-backgrounds**
[COLOR="#0000CD"]lightdm@Xenial:/root$[/COLOR] **gsettings get com.canonical.unity-greeter draw-user-backgrounds**
true
```
As you can see I used the "gsettings get" command to retrieve the current setting, reset to default (true),
then retrieved the current setting again.
No errors.
????

---

### Post by Abdul_Hakim on 2016-05-19
> **vasa1 said:**
> Hi, it would be nice if you post any terminal output within code tags :)

You can select the text you want and then click on the little # sign to have opening and closing code tags flank the text. Or you could just add them by typing them in! The # sign is visible when you start writing a new post. If you don't see the # sign, click on "Go Advanced" just below the posting area.

I've done it for you in one post.

Sorry about that, I thought adding four spaces would work :P



> **CantankRus said:**
> I have used those commands before to change things at the greeter as the user "lightdm" and they still work here.
Just tested...
```
**[COLOR=#006400]glen@Xenial:~$[/COLOR] sudo -i**
[sudo] password for glen: 
root@Xenial:~# xhost +SI:localuser:lightdm
localuser:lightdm being added to access control list
root@Xenial:~# su lightdm -s /bin/bash
[COLOR=#0000CD]lightdm@Xenial:/root$[/COLOR] **gsettings get com.canonical.unity-greeter draw-user-backgrounds**
true
[COLOR=#0000CD]lightdm@Xenial:/root$[/COLOR] **gsettings reset com.canonical.unity-greeter draw-user-backgrounds**
[COLOR=#0000CD]lightdm@Xenial:/root$[/COLOR] **gsettings get com.canonical.unity-greeter draw-user-backgrounds**
true
```
As you can see I used the "gsettings get" command to retrieve the current setting, reset to default (true),
then retrieved the current setting again.
No errors.
????

Idk either. something must've gone wrong somewhere. I even reviewed my bash history to see if I unwittingly made any other changes, but that first command was all I did. I'm just gonna try reinstalling. I'm still on 14.04 so maybe it's a good time to install 16.04

---

### Post by vasa1 on 2016-05-19
> **Abdul_Hakim said:**
> Sorry about that, I thought adding four spaces would work :P
...
That works for markdown. Here bbcode is in use.

---

### Post by CantankRus on 2016-05-19
> **Abdul_Hakim said:**
> Sorry about that, I thought adding four spaces would work :P





Idk either. something must've gone wrong somewhere. I even reviewed my bash history to see if I unwittingly made any other changes, but that first command was all I did. I'm just gonna try reinstalling. I'm still on 14.04 so maybe it's a good time to install 16.04
Sometimes it's best to start afresh. At least you'll know the problem is not caused by something you've done previously.

---

### Post by Abdul_Hakim on 2016-05-20
So I formatted and reinstalled and remounted /home, and now a slightly different issue is occurring. If I use one of the "built-in" wallpapers, then everything works fine. The login wallpaper and matches the desktop wallpaper like it's supposed to. However, if I change the wallpaper to a photo in /home/Pictures, then the issue comes back. The login screen goes back to the ugly default wallpaper and doesn't match my desktop. 

Maybe I could just copy the wallpaper I want into the same directory where the built-in ones are? I never had to do that before but I can give it a try...

So if this is happening even after a fresh install, could there be something in /home that's affecting it? I keep /home on a different partition and just remounted it during the fresh installation

EDIT: Tried copying it over to the /usr/share/backgrounds folder and that didn't seem to work. It doesn't appear in the wallpaper chooser, and when I go to the folder itself, there's no thumbnail it's just a gray X. If I try to click on the photo to open it, it's just a black sqaure.

Ubuntu y u so difficult

---

### Post by Abdul_Hakim on 2016-05-21
Update:

Someone on reddit suggested changing the wallpaper from Firefox. This works, if I change the background from Firefox then both the Desktop and Login wallpapers match like they're supposed to. So that means it's gotta be some sort of permissions and/or groups related thing at this point, right?

Also just noticed that this created a file in /home called Firefox_wallpaper.png, so if LightDM has access to that, maybe the problem isn't my /home folder, but with my ~/Pictures or ~/Pictures/Wallpapers folders... hmm...

EDIT:

Yep, that's the problem. Permissions are all screwy. But at least that I know how to fix :D

---

