---
title: "Autostart does not work, why?"
date: 2014-07-14
forum: General Help
---

### Post by 171742 on 2014-07-14
Hello,

I want to start firefox and grive with autostart, Having put it in into the desktop autostart windows, nothing happens. How to do it? 

(easy please, I am a beginner)

Thanks!

---

### Post by ajgreeny on 2014-07-14
What version of which particular OS are you using and how did you "put it in into the desktop autostart windows"?

---

### Post by 171742 on 2014-07-14
Ubuntu 14.4 lts. I type startup application into the dashboard and add firefox or grive to the box.

---

### Post by coldcritter64 on 2014-07-14
> **171742 said:**
> ...Having put it in into the desktop autostart windows, nothing happens....
Assuming your autostart entry is correct either a logout/login of the desktop or a reboot of the installation will activate an autostart entry. 

Have you restarted the installation or done a desktop logout/login since adding the entries ?

---

### Post by 171742 on 2014-07-14
Hello,

yes, multiple times.

---

### Post by coldcritter64 on 2014-07-14
Try opening your home folder, use "ctrl + alt + h" key combination to show hidden files/folders, open the folders ".config" > "autostart". Look in the autostart folder for a file named firefox.desktop and one called grive.desktop. Are they present ? If they are not but you have added an entry, you may need to check the entries are fully enabled ("ticked" as well as added).

Try using the power button at the top right side of your screen, "Startup Applications" option, to add/check the entries are fully enabled. This last note is just another method to get to the startup applications without using the dash.

---

### Post by 171742 on 2014-07-14
Hello,

both there, how do I "tick" and enable it?

---

### Post by coldcritter64 on 2014-07-14
Go to the power "cog" on the top right of your screen. Select "Startup Applications", then tick the box on the left of the entries you want autostarted.

See the attached screenshot of the same application on my Debian install (gnome-session-properties) as your autostart interface. Note the tick boxes on the left of each entry, you toggle the entry on/off clicking on the tick box.

---

### Post by mc4man on 2014-07-14
What does this show?
```
gedit ~/.config/autostart/firefox.desktop
```

---

### Post by 171742 on 2014-07-15
Hello,

in the "cog" there is no autostart. I attached what is in startup applications and furthermore what comes when I type this line.

---

### Post by Jim_in_Omaha on 2014-12-25
For what its worth,

I ran into a similar issue with three installations of Ubuntu 14.04 and the installation of the grive-tools. The indicator would not automatically startup even though it shows in the startup applications from the Launcher.

So what I tried as a wild hair guess was:

1. Open up the startup applications via the Launcher. This already shows the Google Drive indicator shortcut that does not open and autosync.
2. Click on 'Edit' for the Google Drive.
3. In the Command box I clicked 'Browse' and went to the 

     /opt/thefanclub/grive-tools/grive-indicator

     and basically redid the entry. And it works now.


Then I am also able to get Firefox to autostart along with Gpodder by simply adding from the same Startup Applications panel.

1. Click 'Add'
2. Name it example 'Firefox'
3. In the command box I put just 'firefox' (without quotes, same as if from the command line).
4. Give it a comment if you wish.
5. Click the 'Add' button at the bottom of that panel. Then log out or restart to see if it works.


> **171742 said:**
> Hello,

I want to start firefox and grive with autostart, Having put it in into the desktop autostart windows, nothing happens. How to do it? 

(easy please, I am a beginner)

Thanks!

---

### Post by Todd_Wolfson on 2015-03-13
I have debugged this issue on Linux Mint 17.1 and might be applicable to others. `grive-tools` installs `.config/autostart/grive-indicator-autostart.desktop`. However, after trial/error, it looks like we need to name the file to be the same as others in `.local/share/applications` or `/usr/share/applications/`. To apply the fix I did:

```
mv ~/.config/autostart/grive-indicator-autostart.desktop ~/.config/autostart/grive-indicator.desktop
```

Then, log out and log in to see if it works.

---

