---
title: "New hardware, fresh install and some Compiz questions."
date: 2006-09-11
forum: General Help
---

### Post by MetalMusicAddict on 2006-09-11
Hello all.

I have recently built a [new rig](http://ubuntuforums.org/showthread.php?t=224416). I have a 7900 GT card runnin on Ubuntu with the newiest drivers from nVidia.

I have this system runnin perfect now. I wanna run Compiz but the method I used I gather is outdated.

I know that my Wacom pad didnt like XGL so should I use AIGLX? Would it even make a difference? I thought there was a way to pick the Xsession at GDM. Is that right? Im a little in the dark as to how I should install Compiz now so as to reap all it eye-candy goodness. :) I would also like to try out the AA settings that can now be done.

So if anyone can give me some direction [SIZE="1"][COLOR="DimGray"](Ive searched but I dont know what applies to me now or the best method)[/COLOR][/SIZE] that would be great. I wanna push this card. :)

---

### Post by David Corrales on 2006-09-11
Compiz/XGL is even easier to run now with the compiz-start script and csm.
You basically need to:
[LIST=1]
[*]Get hardware acceleration working
[*]Add Quinn's repo and download the necessary packages
[*]Create the startxgl script and make it executable (sample below)
[*]Create the new session file (sample below)
[*]Set compiz-start to autostart at the System->Preferences->Sessions->Startup Programs menu
[/LIST]

StartXGL script (/usr/bin/startxgl):
```

Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer &
DISPLAY=:1
#Start Gnome
exec gnome-session

```
Run **sudo chown 755 /usr/bin/startxgl** to make it executable.

This is my current session file (/usr/share/xsessions/xgl.desktop):
```

[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl
Icon=
Type=Application

```

---

### Post by MetalMusicAddict on 2006-09-11
Ok. Do I want to use AIGLX or XGL? 

Also is this the right repo to use?
```
deb http://xgl.compiz.info/ dapper aiglx
deb http://xgl.compiz.info/ dapper main
```
Or
```
deb http://www.beerorkid.com/compiz/ dapper main
```

*Then* which packages should I grab? I know there is more than 1 Compiz manager now and a theme manager also. Which do you use?

---

### Post by David Corrales on 2006-09-11
For now, I'd stick with XGL. Nvidia, nor Ati provide the required extensions to fully utilize AIGLX. Also, Nvidia has MUCH better drivers and you can run XGL without problems.

Although both xgl.compiz.info and [www.beerorkid.com/compiz](www.beerorkid.com/compiz) contain the same packages (they're sync'ed on updates), once the xgl.compiz.info one became out of sync and caused trouble. I rather not be able to update for a day or two than screwing up my packages again so I only enable the beerorkid one. Don't forget to add the authentication key :)
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -

```

Packages:
```

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd csm

```

I think you should be set with those. There's the compiz-vainilla but that one doesn't have Quinn's patches so it's less up to date.
CGWD is the compiz-gnome-window-manager which has all the cool themes :)! Also, there's a new app called CSM (compiz settings manager) which allows easy editing of the plugins settings.

---

### Post by MetalMusicAddict on 2006-09-11
So then this will let me at GDM pick a XGL or non-XGL session right?

```

[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl
Icon=
Type=Application

```

I still play games and my Wacom pad has trouble with XGL.

---

### Post by David Corrales on 2006-09-11
Yep, that will give you an extra entry at GDM so you can choose between a regular or XGL session.

---

### Post by MetalMusicAddict on 2006-09-11
Thanx man. Ill let you know how it goes. ;) I still gotta figure out how to do antialiasing.

---

### Post by MetalMusicAddict on 2006-09-11
I hit a snag. Heres what Im gettin when I try to log in:
> 
Xsession: unable to launch "/usr/bin/startxgl"
Xsession --- "/usr/bin/startxgl" not found; falling back to default session.

Heres what I did. In order.

[LIST]
[*]Added **deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main** to my sources.list
[*]Did a **sudo gedit /usr/bin/startxgl** and added what you posted for that.
[*]Did a **sudo gedit /usr/share/xsessions/xgl.desktop** and added what you posted for that.
[*]Then **sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd csm cgwd-themes**
[*]Reboot.
[/LIST]

I tried to pick XGL at GDM then it gave me that above message. When was I supposed to do this:
> 5. Set compiz-start to autostart at the System->Preferences->Sessions menu

When I log into the XGL session or when? And what order? 40? 50?
Was I supposed to make something executable? Like **sudo chmod 755 /usr/bin/startxgl**?

---

### Post by David Corrales on 2006-09-11
You gotta make /usr/bin/startxgl executable :)
Type **sudo chmod 755 /usr/bin/startxgl** to get that taken care of.

About the session, go to *Startup Programs* inside the *Sessions* applications. There, just click on add and browse for the /usr/bin/compiz-start file, that should do it.
You can do this step inside a regular gnome session or an XGL one. Remember that compiz is just a window manager.

---

### Post by MetalMusicAddict on 2006-09-11
1 step forward then 1 step back. I got logged in. YAY! But now when I added compiz-start to the session startup I get that "Your session has lasted shorter than 10 secs" error. If I run compiz-start manually, it all crashes.

Heres my .xsession-errors log:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "atm"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/dash:/tmp/.ICE-unix/5594
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(nautilus:5667): Eel-CRITICAL **: eel_pango_font_description_get_largest_fitting_font_size: assertion `maximum_acceptable_font_size > minimum_acceptable_font_size' failed

```

---

### Post by David Corrales on 2006-09-11
Ok, so for now you can log into XGL but without compiz?

---

### Post by David Corrales on 2006-09-11
nt

---

### Post by MetalMusicAddict on 2006-09-11
> **David Corrales said:**
> Ok, so for now you can log into XGL but without compiz?

Exactly. :) And thanx for the help so far.

---

### Post by David Corrales on 2006-09-11
Why don't you try upgrading packages first to see if that helps?
[B]sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by MetalMusicAddict on 2006-09-11
Yea. I did. No luck. Im lookin around Compiz-Fourms now but I dont see anything yet.

EDIT: I see many people are havin this problem now. Thanx so much for getting me this far. Ill keep up with the threads over there.

[HERES]("http://www.compiz.net/topic-3265-compiz-crash-under-xgl") the one that tipped me off.

I wonder if it has to do with me not using the repo nVidia drivers?

---

### Post by David Corrales on 2006-09-11
I'm using the standard repo drivers without problems. Maybe you can try downgrading and see if it helps.

---

### Post by MetalMusicAddict on 2006-09-11
> **David Corrales said:**
> I'm using the standard repo drivers without problems. Maybe you can try downgrading and see if it helps.
Ill try but the thing is my card is so new those drivers dont work as well as the new ones from nVidia.

---

### Post by David Corrales on 2006-09-11
Hmmm wait a bit for updated packages if you can't move back to other drivers then =/ damn, too bad you can't run it right away :(

---

### Post by MetalMusicAddict on 2006-09-11
Hell. Im not sure how to *not* use the compiled drivers. I cant blacklist "nvidia" that wouldnt let the repo one start either. :-k

---

### Post by David Corrales on 2006-09-11
You can use the regular nvidia driver (non-accelerated) then remove all the compiled stuff and install from the repos. But if that won't help... lol

---

