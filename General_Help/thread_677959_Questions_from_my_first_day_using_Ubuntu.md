---
title: "Questions from my first day using Ubuntu"
date: 2008-01-25
forum: General Help
---

### Post by bobbo85 on 2008-01-25
Hi everyone, I'm a newbie to Linux as of yesterday - have been using Windows my whole life and am excited to get going on Ubuntu.

That being said, here are some issues I've had and questions I have:

1)  What is your "routine" for getting up and running with Ubuntu? I mean, what applications do people typically use? What changes do I need to make from the defaults to get going (checking off that other 'pository box in the add/remove application window to show a bigger list of apps for example)... 

What I mean by that last part is this: You know how when you first install windows you have to de-crappify it? I have a pretty standard routine for getting someone going on a new windows PC, so they can watch movies, listen to music, go to websites that use flash, pretty basic stuff. I kind of show them what stuff I usually use, what modifications I make, what tips and tricks help save them time, etc.  So think of that "let me show you the ropes" kind of angle.

2)  Can someone please tell me some of the pros and cons of a few popular apps in of these types?:
-Instant Messaging (currently using MirandaIM in windows for its customizations)
-Music (currently using Winamp for customizations)
-Video (Currently using VLC media or Windows Media player, I just watch movies full screen)
-Desktop add-ons (Currently using Rainlendar Calendar, Stardock ObjectDock, and UXtheme to use custom themes with XP - would like to see what other tools are useful)

3)  RhythmBox added songs to my iPod and could play them from the iPod, but when I ejected the iPod it showed 0 songs... back in windows, iTunes had to reformat the ipod and start all over.  What do I have to do to get this to work?

4)  Customizing pidgin... are the GDK themes system wide?  I mean are they the equivalent of setting a windows theme?  Or can I just use the theme on the Pidgin program?  If so, how do I do it?  Or if I should use a different program altogether, which one do you recommend?

Thanks in advance for any replies.

---

### Post by zeller on 2008-01-25
Well, I can add that VLC is a must for Linux as well. You should be able to find it in the repos after install. I believe the proper code would be:

```
sudo apt-get vlc
```

I can't really help with the rest though, I'm still learning myself.

---

### Post by Najmudin on 2008-01-25
I will share with you my experience with music players in ubuntu , go to synaptic and search for Audacious 
it will give the result so check the boxes of these :
- audacious
- audacious-crossfade
- audacious-plugins
- audacious-plugins-extra
then search for : 
- tap-plugins
- caps
check the boxes , and press apply to install them all.
after that open audacious , right click on its interface and select preferences > select the audio tap from the left side > output plugin preferences and check the box of " use software volume control" 
next go to plugins tap , you will finde many plugins you can customize or discover by your self , but i will give you my sitting whick gives me a great sound : select the effect tap > check these boxes
- AudioCompressor AGC ... ( leave the setting as it is )
- Extra Stereo plugin ( customiz it as you like)
-LADSPA host > select preferences button > a long list will apear > just chose " CAPS : Plate - Versatile plate reverb" add it to the running plugins > press Configure button > another window will apear set the paramiters to this :
- bandwidith :  0.914
- tail : 0.699
- damping : 0.300
- blend : 0.250
This is my setting ,but off course you can change it as you like or maybe you don't like reverb sound.
Finishing these steps and you will get a great music player similar to winamp and you can customize it as you like ( you can use the classic winamp skins for it) , i tried many music players in ubuntu but i found audacious to be the best with its many features , this is may opinion.
About the iPod i read some where that amarok is great in case of dealing with iPods , but i don't own one so I cant help you with that.
About the widgets you can use "screenlet" here is a link on how to install it
[http://osnovice.blogspot.com/2007/04/gadgets-widgets-no-screenlets.html]("http://osnovice.blogspot.com/2007/04/gadgets-widgets-no-screenlets.html")
You can find many screenlets in this site also:
[http://www.gnome-look.org/]("http://www.gnome-look.org/")

I hope that will help you , and have a good time with Ubuntu.:popcorn:

---

### Post by zvacet on 2008-01-25
1.**Repositories**

System>administration<software sources>chek all boxes under Ubuntu software tab and under updates tab.Reload.Now you have all repos open and you can install anything from Ubuntu repos.

2.**Restricted formats**

```
sudo apt-get install ubuntu-restricted-extras
```

With this you will get Java,flash,plugins...

3.**Adding repositories**

Programs<accessories<terminal

```
gsudo gedit /etc/apt/sources.list
```

add this 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save the file.

Again in terminal

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update

now go to the synaptic and search for w32(or 64 if you use 64 bit version)codecs and install them.That is all I can think of right now.With all this you should be able to play with your ubuntu castumization and make it look lik you want too.

if you are used to winamp try **xmms**(it is in synaptic)
Same for movies.If you are familiar with VLC just install it with synaptic.You can try Mplayer if you feel like it.

Go to the synaptic and install **build-essential** and **alien**.

---

### Post by Therion on 2008-01-25
[Thirteen Things to Do]("http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html") Immediately After Installing Ubuntu.

One person's idea (not mine) of what constitutes the [Top-10 Ubuntu Apps and Tweaks]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php").

---

### Post by oldos2er on 2008-01-25
FWIW, here's a list  of packages i grab after a new install:

 ubuntu-restricted-extras
libdvdcss2
exaile
slrn
glunarclock
glipper
catfish
vlc
build-essential
boinc-client
boinc-manager
checkinstall
auto-apt
cairo-clock
compizconfig-settings-manager
emerald
filelight
nautilus-gksu
nautilus-open-terminal
nautilus-actions
nautilus-wallpaper
transcode
streamripper
subversion
sysv-rc-conf
zsh
gmail-notify

 You need to enable all repositories, including source and Medibuntu, to get all these.

---

### Post by rosegarden78 on 2008-01-25
Basically I start with a Vista/OSX style:

1) Install Ubuntu Desktop GG 7.10
2) Goto Synaptic package manager
3) Search for "compiz"
4) Install all programs (including compiz-kde) with compiz in the name:
---except one will ask you to un-install compiz
---do not install this one package
5) Run compiz by pressing Alt-F2

If all went well you now have Vista eye candy.  Only it's much, much more powerful than just candy.  You can have nine viewports, fancy switching, expo, etc.  But now you want a Mac style desktop.  You need Avant Manager on an XFCE desktop.  You might also want to run nautilus when using Xfce.  If you don't want Xfce to manage your desktop un-check that option in Menu - Settings - Desktop Settings and you'll have a blackbox with a dock and eye candy.

1) Launch Synaptic
2) Search for "xfce"
3) Install xfce
4) Log out or press Ctrl-Alt-Backspace
5) Session XFCE session
6) Log in

Depending on version you'll either see two panels like Ubuntu or just one button.  Either way you can remove all panels but one by right clicking properties.  I like to reduce my panel to 16 px with only the following applets: menu, volume control, system tray, nm-applet, clock.  I like to un-expand the panel and fix placement on bottom right with 100% transparency, auto-hide and make opaque selected.

Click here to finish the project.
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Finally add the programs you need some to consider are:

1) Fluidsynth
2) Rosegarden
3) FFMPEG
4) GIMP
5) Inkscape
6) CellWriter
7) Kruler
8) Opera web browser 9.5 beta
9) Flash plugin - nonfree
10) Restricted extras
11) Extra sound fonts from Hammer Sound
12) Katapult
13) Audacity

Finally add the Mac Leopard galaxy background and you have the same desktop they showed on the commercial for the super-slim notebook!  Keep in mind, though, ABC.com still uses OS-sniffing to block Linux.  If you want to get streaming HD video they insist you access with Windows or Mac.

EDIT: I figured out how to get streaming HD in Ubuntu!  [http://ubuntuforums.org/showthread.php?t=679165](http://ubuntuforums.org/showthread.php?t=679165)

---

