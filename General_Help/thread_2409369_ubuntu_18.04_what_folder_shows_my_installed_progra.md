---
title: "ubuntu 18.04 what folder shows my installed programs?"
date: 2019-01-01
forum: General Help
---

### Post by seekertom on 2019-01-01
Happy New Year, Y'all!
I'm running ubuntu 18.04. Has been running with no issues unti I think hd problems, plus my impatience...
I chose to install some updates now and icon for activity showed up in favorites list. I'm assuming the updates were in progress.
I wanted to use dosbox at same time so clicked on its icon in favs. No response so clicked again. Still no response.
At this time, totally forgetting about update in progress I restarted my pc in normal manner.

After booting to the grub menu(?) I let it continue on its own. Usually system just boots to login screen. This time I got the black and white screen with lots of error messages about not finding stuff, and ending with suggestion run fsck.
I tried fsck a few times with no success. Then rebooted a few times trying different grub menu options, all with same results... run fsck.

Ok, so sounds like hd crashed.
I added a good, booting ubuntu 18.04 hd and booted system ok, with access to the original hd using files.
I copied what I could to a new folder on current boot drive, including desktop, documents, downloads, music, pictures snap and examples. I was not sure about snap and examples, but copied anyhow.
I just wanted to redo my original hd and preserve as much as I could by copying stuff off to another drive. ( I tried install from cd but saw no way to 'refresh' ubuntu or reinstall preserving docs etc, so went with shotgun method... )
At this point I dont remember all the interesting programs I might have installed originally, and was hoping to locate a folder where all my apps are listed, which is the goal of this post.

Barring a brilliant suggestion on how I might easily repair original hd problem without all this, can anyone tell me what folder to look in to find all my original apps and save a list of them?

Thanks for you help.
seekertom
):P

---

### Post by him610 on 2019-01-01
You should be able to open Software to view Installed applications.

---

### Post by dragonfly41 on 2019-01-01
From Live CD I would try running boot-repair on the original failed drive.
From memory I think you will need to install boot-repair in the Live CD instance.

---

### Post by yancek on 2019-01-01
> This time I got the black and white screen with lots of error messages

Best thing to do in a case like that is to write down the error/warning messages or take a photo of the screen if possible.  Otherwise, all we can do is guess.
What exact command did you use to do a filesystem check?

You could try running boot repair (see the link below) and using the 2nd option to use the ppa from the Ubuntu install DVD/USB.  Make sure you select the option to Create BootInfo Summary and not try to do any repairs and post the link you get when it finishes here.  That will give members here information which may help resolve the initial problem.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by seekertom on 2019-01-01
and what might be the path to the 'software' folder from 1.5tb volume shown under 'other locations' from files???

---

### Post by him610 on 2019-01-01
To make a listing of installed software
```
sudo dpkg -l > installed_software.txt
```
or you could also look in Synaptic Package Manager (Status, Installed)

---

### Post by again? on 2019-01-01
On the mounted volume look in **/usr/share/applications**.
This is the main location for launchers of graphical applications. 
Also look in /opt.

---

### Post by seekertom on 2019-01-02
thanks, guber2. this helps.
st

---

### Post by seekertom on 2019-01-02
[LEFT]thanks for the help. listed what I need to reinstall, got copy of all my misc docs on another drv, reinstalled 18 from cd and am now good to go.
lesson learned: during an update, go get cuppa, do not reboot!
hny! st
[/LEFT]

---

### Post by HermanAB on 2019-01-02
Another way to look at it:  An upgrade/update must be earned.

If your computer is running properly and you have not heard of serious security issues on the horizon, then doing an update cannot make the machine better.  It will be the same, or worse.  So, think before you leap.

---

### Post by again? on 2019-01-02
> **seekertom said:**
> [LEFT][COLOR=#222222][FONT=Verdana]thanks for the help. listed what I need to reinstall, got copy of all my misc docs on another drv, reinstalled 18 from cd and am now good to go.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]lesson learned: during an update, go get cuppa, do not reboot![/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]hny! st[/FONT][/COLOR][/LEFT]
Now what you want to do is add the new packages you install to a script for next time you install.
eg this is my **myapps.sh** script...
```
#!/bin/bash

sudo apt install artha conky-all curl dconf-editor easystroke galternatives gedit-plugins glipper gnote gpodder gtk-redshift hddtemp inxi keepassx kupfer libsox-fmt-all lm-sensors man2html nemo p7zip-full p7zip-rar shutter smplayer sox speedtest-cli synaptic undistract-me vlc w3m wmctrl xclip xdotool xsel zsync ttf-mscorefonts-installer lolcat chrome-gnome-shell gnome-icon-theme-gartoon-redux gnome-tweak-tool python-pip yad ppa-purge
echo
read -n 1 -p "Press any key to exit this script..."
```

---

