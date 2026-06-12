---
title: "Can not save settings from Dconf Editor  or Unity Tweak Tool"
date: 2016-09-10
forum: General Help
---

### Post by irv on 2016-09-10
I can make changes in Dconf Editor and Unity Tweak Tool, but they do not stick. When I reboot it goes back to default setting. The only thing I can find that's happening is an error log in .xsession-errors.
> openConnection: connect: No such file or directory
cannot connect to brltty at :0
I don't know if this has anything to do with not being able to retain changes?
Edit: I am using Unity desktop with Ubuntu 16.04.

---

### Post by nothingspecial on 2016-09-10
Hey Irv :)

You should probably give an example of one or two of the the changes you are trying to make, that would make it easier to for someone to help.

---

### Post by irv on 2016-09-10
[ATTACH=CONFIG]271060[/ATTACH][ATTACH=CONFIG]271061[/ATTACH]
On the Unity Tweek Tool, I put a check mark in the large mouse pointer and set it to black.
In the Dconf Editor, I set the mouse size to 48 and again, black.
When I reboot I am back to the small and white arrow for a pointer.

---

### Post by mc4man on 2016-09-10
Those 2 settings will not be persistent, upon restart or log out/in they will return to the defaults.
One, the cursor-theme, is (re)set to the value defined in 10_ubuntu-settings.gschema.override
The other, cursor-size, is (re)set to the value in  org.gnome.desktop.interface.gschema.xml
(both files are in /usr/share/glib-2.0/schemas

So to change persistently you'd need to find a different method than what you're currently doing. One way would be to edit those 2 files to suit & compile schemas to set new defaults. Instructions upon request if you can't find a different method.

---

### Post by irv on 2016-09-10
> **mc4man said:**
> Those 2 settings will not be persistent, upon restart or log out/in they will return to the defaults.
One, the cursor-theme, is (re)set to the value defined in 10_ubuntu-settings.gschema.override
The other, cursor-size, is (re)set to the value in  org.gnome.desktop.interface.gschema.xml
(both files are in /usr/share/glib-2.0/schemas

So to change persistently you'd need to find a different method than what you're currently doing. One way would be to edit those 2 files to suit & compile schemas to set new defaults. Instructions upon request if you can't find a different method.

I never tried this before, but if had Instructions I would give it a try.

---

### Post by mc4man on 2016-09-10
You need to carefully edit both files in a root editor, here I use nano or if desired you can use gedit if opened with 
sudo -H gedit /path/to/file (or any other means to properly use gedit as root, do not use sudo gedit command

For reference & line numbers see screens [here]("https://ubuntuforums.org/showthread.php?t=2317532&p=13536875&viewfull=1#post13536875"), in those I set  to 26 & DMZ-Black
(the forum isn't letting me attach a screenshot in this thread... I had a thread to dump screens in but it was jailed.

After editing & saving both files run this command, it _must run without error or comment_. If there is any error or comment then fix & rerun command until it runs without error or comment before logging out or restarting. If you edit carefully & correctly there will be no error or comment.

Then log out/in & see.
 ```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

---

### Post by irv on 2016-09-10
Worked flawless. I made the changes to both files Theme and size as super user save changes and re-compile with the command you gave me and it worked great. After rebooting I have a large black arrow.
Before doing this when the mouse when over the browser it got small again but now it stays big. Makes it easier to find on the screen.
Thanks for the help mc4man, and I will mark this thread solved.

---

### Post by #&amp;thj^% on 2016-09-10
@mc4man=d>" title="Applause">

---

### Post by irv on 2016-09-10
Trying to understand the command.
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
I know the sudo is super user do and I believe the glib-compile-schemas parts compiles the files in the directory  given in the last part of the command.
Am I right?

---

### Post by mc4man on 2016-09-10
if you were to look you'd see /usr/share/glib-2.0/schemas/gschemas.compiled
That is the binary of all the schemas & what is used.
The reason for making sure the command works correctly is if a schemas fails then either the 'bad' key or sometimes the whole schemas itself will be ignored upon next login. In many cases that would be highly undesirable. So any mistake must be corrected while the current settings are in memory.

If for some not likely to happen  reason those files are replaced with an update/upgrade then you'll need to repeat process.

---

### Post by mc4man on 2016-09-11
Another way would be to just leave the gnome .xml alone or as is  & add an override to the ubuntu override file for cursor size.
The syntax would follow the override file so like this - 
```
[org.gnome.desktop.interface]
gtk-theme="Ambiance"
icon-theme="ubuntu-mono-dark"
cursor-theme="DMZ-Black"
cursor-size=28
font-name="Ubuntu 11"
monospace-font-name="Ubuntu Mono 13"
```

Now originally tried - 
cursor-size="28"
which produced - 
> $ sudo glib-compile-schemas /usr/share/glib-2.0/schemas
error parsing key 'cursor-size' in schema 'org.gnome.desktop.interface' as specified in override file '/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override': 0-4:can not parse as value of type 'i'.Ignoring override for this key.
Basically saying couldn't parse an integer.  What fixed was to remove the quotes & rerun command

---

### Post by irv on 2016-09-11
mc4man, thanks for the explanation. This has been very enlightening.
Many years ago when I was still in the workforce I took some classes on computer architects where I learn about interpreted and compiled languages, and the differences.
I know that sometimes these changes will change if I do an update, so I thought about using a command to change these settings on the fly at start up. Like putting a command in the startup application, but for now this will work for me.

---

### Post by philip73 on 2016-10-28
Thanks mc4man the itsy cursor on my HTPC was driving me nuts...phil

---

### Post by irv on 2017-04-14
I thought I would update this thread because things are changing. I upgraded to Ubuntu 17.04 and am using Gnome desktop and when I change the size of the Mouse Pointer in Dconf Editor it keeps on a reboot on both my laptops Dell and Asus.

---

