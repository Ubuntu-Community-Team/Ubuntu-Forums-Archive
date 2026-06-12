---
title: "Customize Login Screen - Ubuntu 14.04"
date: 2015-04-29
forum: General Help
---

### Post by GrouchyGaijin on 2015-04-29
Hi Folks,

I know that there are a few different threads here and articles at other websites about customizing the login screen in Ubuntu 14.04, however after reading many different posts and recommendations I am still not able to customize my login screen.

Just to be clear, by login screen I mean the screen where you type in your password and by customize I mean use a wallpaper other than the wallpaper that is on the desktop once I have logged in.

Has anyone been able to successfully change the login screen wallpaper?  If so, how exactly did you do so?
In the dconf editor I have changed the path to the image I want to use, yet the login screen continues to use the desktop wallpaper.  See the attached scrot for my deconf editor settings.

I realize that this is a trivial issue that pales in comparison to other issues discussed here, nevertheless, any help would be appreciated.

---

### Post by deadflowr on 2015-04-29
I've never changed the path in the dconf settings, but my dconf settings has the draw-user-background checked.
And to use user-pictures you need to set the permissions of the picture for other(s) to read/read-only, at least.

---

### Post by GrouchyGaijin on 2015-04-29
Thanks - I rechecked the box labeled draw-user-backgrounds and made sure that my desired image is readable by others.  However, the login screen still uses the desktop wallpaper as the background.  How, specifically are you telling Ubuntu which image to use?

---

### Post by deadflowr on 2015-04-29
I open Appearance, I toggle the Wallpaper option to the Pictures option, or click on the plus button, and choose/add my picture.

You might check to see that the full path way to the picture is readable for other.
make sure /home/you/Pictures are all readable.
I think if the pictures are readable but the folder that they are in are not, then it cannot see them, since it cannot read what is in the folder.
If that makes sense.

---

### Post by GrouchyGaijin on 2015-04-29
> **deadflowr said:**
> I open Appearance, I toggle the Wallpaper option to the Pictures option, or click on the plus button, and choose/add my picture.



It sounds like we are talking about two different things.  It sounds like you are talking about changing the desktop wallpaper.
I am talking about changing the background of the login screen before you actually get to the desktop.  Although, I've misunderstood things in the past and I may be misunderstanding now.

---

### Post by deadflowr on 2015-04-29
Yeah my eyes are seeing what they want.
Now after re-reading post#1 do this:
From here
[https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper](https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper)

You might need to create the file
> /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
I used gedit
```
gksu gedit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```
and add the loines mentioned
```
[COLOR=#333333][com.canonical.unity-greeter]
[/COLOR][COLOR=#333333]draw-user-backgrounds=false
[/COLOR][COLOR=#333333]background='/path/to/wallpaper.png'
```
make sure that you use the quotes to encapsulate the path, if that makes sense.
It erred for me when trying without quotes, so watch for that.
Then run the last command listed
[/COLOR]```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
and logout to see if the change happened.
It did for me.
Hope it does for you.

---

### Post by GrouchyGaijin on 2015-04-29
hmmm I followed your advice, including making sure that the quotes to encapsulate the path and then I restarted.  I still have the desktop wallpaper being used as the background for the login screen.
I am wondering though, I usually use Unity, but have Gnome installed as well.  I noticed, according to Synaptic that I have both: **unity-greeter **and **lightdm-gtk-greeter** installed.  I wonder if that could be causing a problem?  If I remove the lightdm-gtk-greeter will I still be able to login to Gnome?

---

### Post by deadflowr on 2015-04-29
Which log in screen was in use?
lightdm-gtk-greeter looks like the older variant, with the login window in the middle of the screen, where as unity-greeter has the login window area toward the left side area.If that makes sense.

But YES, you can still log into the gnome session without the lightdm-gtk-greeter.
You do not have to uninstall it though.
The link I provided also tells you how to set a default greeter.

I would recommend scrolling up to the top to get a full idea of how lightdm works.
Basically the easy way is to make the /etc/lightdm/lightdm.conf.d/50-myconfig.conf file.

Use this file to add your personal configurations because this file won't get overwritten if some odd update from lightdm comes around.
Where as the files in /usr/share/lioghtdm will.
Updates for config files in the /etc folder will give you a warning if a new one is available, and whether or not to use the new one or keep the old one.

But basically make the file
```
gksu gedit /etc/lightdm/lightdm.conf.d/50-myconfig.conf
```
and add
```
[SeatDefaults]
greeter-session=unity=greeter
```
save and the system should look there and use whatever setting for the greeter you choose.

 Does that make any sense?

---

### Post by GrouchyGaijin on 2015-04-30
It's good to be back :-)

Well, I attempted to follow your suggestions and had some difficulty - LOL.

1. Looked at the login screen and thought:"This login box seems to be dead on in the middle of the screen."
2. I *attempted* to run ```
gksu gedit /etc/lightdm/lightdm.conf.d/50-myconfig.conf
```
3. Actually, the command ran fine. The problem was that I could not save the file.
4. I thought "hmmmm there does not seem to be a directory called **lightdm.conf.d**.  Why don't I make one?
5. I created said directory using ```
sudo mkdir 
``` and then created 50-myconfig.conf inside that directory.
6. I then set the contents of the 50-myconfig.conf file to: ```
[SeatDefaults]
greeter-session=unity=greeter
```
7. With a sense of confidence I rebooted, although looking back I suppose the fact that a simple logout was taking a very long time was a harbinger of issues to come.
8.  I was told that my graphics (settings? hardware? - it's a blur now) could not be detected and that I must reconfigure them ***myself***.  That did not sound good.
9. But wait, I had the option of running in low graphics mode - that will work, just this one time I thought.
10. The low graphics choice initiated a loop in which I couldn't login, because the login screen could not be displayed so Ubuntu would try once again to display the login screen which could not be displayed....
11. Hold down the power button and try again - this time I chose boot to console.
12.  Sensing that 30 minutes is simply too long to boot, I once again hit the power button to restart the machine. (Note: I did *not* sit there watching the machine for 30 minutes - LOL)
13. When I realized that booting to the console was going no where, I began The Hunt.  That is, I was looking for an Ubuntu live CD.  After a long search I found an old 10.10 CD that I didn't even know I still had.
14.  I booted the 10.10 CD and navigated to** /etc/lightdm/** where I removed the offending files that I had created earlier along with their lair - the lightdm.conf.d. directory.
15. I rebooted.
16. I *could* once again login although now there was a problem with gnome-shell.  I am not sure what the problem actually was as when I clicked for more details, I read that there had been a crash.  Ah **THAT** explains it.
17. I reinstalled gnome-shell and rebooted.

I seem to be able to login now without a crash.  However, despite the fact that I do not often use gnome-shell I am afraid to remove it out of fear that the problem is that there is something very wrong with my unity-greeter configuration and without being able to use the lightdm-gtk-greeter I will not be able to login at all.

---

### Post by TheFadedBrit on 2015-04-30
Id of thought it would be as easy as changing the line to the directory the files are in however i may be wrong :/

---

### Post by GrouchyGaijin on 2015-04-30
> **TheFadedBrit said:**
> Id of thought it would be as easy as changing the line to the directory the files are in however i may be wrong :/

Hi Brit,

I can't tell if you are being sarcastic or not, but which line exactly would you change?  As it is now, I am almost afraid to mess with the login screen any more, because I really like being able to login to my system. :)

---

### Post by deadflowr on 2015-04-30
```
[SeatDefaults]
greeter-session=unity=greeter
```

My Bad.
This is a typo.
Should be
```
[SeatDefaults]
greeter-session=unity-greeter
```
dash sign, not equal sign.
Whoops.

As far as saving and not having the folder, at least with gedit you can use the Save As function then navigate to the /etc/lightdm directory and then use the Create Folder option to make the lightdm.conf.d folder, then save the file.
And the file name can be anything you want to call it, as long as it has the number in front and .conf at the end. So if you to call it 10_bababooey.conf, if you want.

Though I do not know if the messed up unity=greeter line caused the graphics problem. I know it was an error.
And I'm not sure if this will be of any help, really.

---

### Post by GrouchyGaijin on 2015-04-30
Thanks - I'll give it a try later tonight :)

---

### Post by CantankRus on 2015-04-30
Hi GrouchyGaijin,
LightDM does not configure the look of greeters. To set the backgroung image you need to configure the  appropriate greeter.
In Ubuntu/unity this is the unity-greeter.
[ATTACH=CONFIG]261669[/ATTACH]
If you remove the **lightdm-gtk-greeter** you will default to using the **unity-greeter** if it is installed.

Unity Greeter by default shows the currently selected users background. To set one default background and stop the switching, 
edit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```
gksudo gedit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```
```
[com.canonical.unity-greeter]
draw-user-backgrounds=false
background='[COLOR="#808080"]/path/to/wallpaper[/COLOR]'
```

eg my file
```
[com.canonical.unity-greeter]
draw-user-backgrounds=false
background='/home/glen/Pictures/pebbles.jpg'
```
****Use a pic with the same resolution as your screen****

Save and close your file and run...
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
The new wallpaper should show when you logout.

The Lock screen gets it's image from **com.canonical.unity-greeter background** where now the default image path for this key 
is whatever you set in your greeter override file.
```
gsettings get com.canonical.unity-greeter background
```

So if you want your Lock screen to be the same as your current desktop background, run this command.
```
gsettings set com.canonical.unity-greeter background "$(gsettings get org.gnome.desktop.background picture-uri | cut -c 9- | tr -d "'")"
```

To revert, just comment the 2 lines in your override file and run the **glib-compile-schemas** command again.

---

### Post by GrouchyGaijin on 2015-04-30
Thank you for the really useful and easy to follow instructions.  It seems, based on the fact that my current login box is in the middle of the screen, that I am using gnome's greeter despite logging into unity. (I also have gnome shell installed.)  Do you happen to know how I can confirm which greeter is in use?

---

### Post by CantankRus on 2015-04-30
> **GrouchyGaijin said:**
> Thank you for the really useful and easy to follow instructions.  It seems, based on the fact that my current login box is in the middle of the screen, that I am using gnome's greeter despite logging into unity. (I also have gnome shell installed.)  Do you happen to know how I can confirm which greeter is in use?

Look in /usr/share/lightdm/lightdm.conf.d
The files in here are accessed in numbered order and will override previous files.
I just installed lightdm-gtk-greeter which is installed when you install gnome-shell.
The pic shows how lightdm-gtk-greeter changes the greeter-session.
[ATTACH=CONFIG]261673[/ATTACH]
Uninstall lightdm-gtk-greeter and you return to using **50-unity-greeter.conf** (gnome-shell will still be accessible)

lightdm-gtk-greeter (pic) looks a lot different than the unity-greeter.
[ATTACH=CONFIG]261674[/ATTACH]

---

### Post by GrouchyGaijin on 2015-04-30
and we have a winner!
Thank you so much guys, I appreciate the help.

I just uninstalled lightdm-gtk-greeter and restarted.  The login screen is now the image I wanted to use.
I do have a couple of follow up questions though.

1. How did you take a scrot of the login screen?
2. The image I specified in lieu of the Ubuntu logo ***is ***showing up on the login screen, but way down in the corner of the new wallpaper.  The logo image is only about half visible.  Is there a way to adjust where the logo is placed on the login screen?

---

### Post by CantankRus on 2015-04-30
> **GrouchyGaijin said:**
> and we have a winner!
Thank you so much guys, I appreciate the help.

I just uninstalled lightdm-gtk-greeter and restarted.  The login screen is now the image I wanted to use.
I do have a couple of follow up questions though.

1. How did you take a scrot of the login screen?
2. The image I specified in lieu of the Ubuntu logo ***is ***showing up on the login screen, but way down in the corner of the new wallpaper.  The logo image is only about half visible.  Is there a way to adjust where the logo is placed on the login screen?
1. You can run **lightdm --test-mode** in terminal.(needs xserver-xephyr) You can interact with the menus. ctrl+c in terminal to kill.
2. Don't know.  Haven't looked at any more than setting the background.

---

### Post by TheFadedBrit on 2015-05-01
No i was generally being honest about it... sorry for the confusion anyway from my expreinence with ubuntu and the likes i think it is just as simple of changing the destination and file name that the login screen uses.


However please make a backup id feel really bad if you killed your install.. :mad:

Take care

Faded.

---

### Post by TheFadedBrit on 2015-05-01
Glad to see its working and that!

well done lads and ladies!

Faded

---

