---
title: "All nautilus windows opens as root. How to stop it"
date: 2014-09-06
forum: General Help
---

### Post by michael_hansen2 on 2014-09-06
I'm not sure how this happened, but every single nautilus window that I open opens as root. It doesn't matter if I start them from the unity search bar or click an icon. I have literally searched EVERY WHERE and every single post I find is on how to make nautilus open as root which is easy and not my problem. I want it to *not* do that.

I tried upgrading my ubuntu incase that would fix it (Yeah, I was desperate), but even in Ubuntu 14.04 this happens. This is literally the first issue in years where I could not find a solution myself so I'm pretty desperate here.

Any ideas?

---

### Post by deadflowr on 2014-09-06
Does anything else open as root?

---

### Post by michael_hansen2 on 2014-09-06
No, not that I'm aware of although I'm not sure how to confirm that. I tried forcing LibreOffice to open as root and it doesn't say "root" in the title so I don't know for sure. Terminal definitely does not open as root as that's easy to confirm. Do you want me to confirm some specific programs?

---

### Post by ibjsb4 on 2014-09-06
Right click on your nautilus launcher and go to properties.  What command is it using to launch a session?

---

### Post by michael_hansen2 on 2014-09-06
See that's the odd thing. I lost the launcher in my unity menu so the way I launch it now is either type "Home" in unity search  bar or just click one of the folders on my desktop and then go where i need to go.

---

### Post by ibjsb4 on 2014-09-06
Ok, go to /usr/share/applications and look up the properties.

If its not listed under 'nautilus', look for 'files'.

---

### Post by michael_hansen2 on 2014-09-07
Nautilus didn't exist, but there was 2 "Files". Both had these settings:

Owner: Me
Access: Read and write

Group: Root
Access: Read-only

Others: Read only

I looked up a few other programs such as FileZilla, Calculator & Firefox and they all had the same settings

Any ideas? I assume the culprit is the group, but I didn't change anything to be on the safe side.

---

### Post by CantankRus on 2014-09-07
Files here should be owned as root.
Done anything related to permissions or logging on as root?

Open a terminal and run nautilus.
Paste what you see in terminal.
eg
```
**glen@Trusty:~$** nautilus
Initializing nautilus-open-terminal extension
```

Is nautilus root?

---

### Post by michael_hansen2 on 2014-09-07
Not that I'm aware of no. I use gksudo from time to time, but I don't recall anything specific that would have caused it. 

Output of nautilus is blank in termnial, but it is not run as root if I run it from terminal.

---

### Post by mc4man on 2014-09-07
Maybe try this - 
```
cp /usr/share/applications/nautilus.desktop ~/.local/share/applications/
```
Then log out/in
Once logged back in go - 
alt+F2 > gtk-launch nautilus

If it open normally then right click on the unity launcher icon > lock to launcher

If it doesn't then 
gedit ~/.local/share/applications/nautilus.desktop 
and post

---

### Post by CantankRus on 2014-09-07
Run 
```
echo $USER
```
and **paste output**
eg
```
glen@Trusty:~$ echo $USER
glen
```

When running as a normal user you should see as in pic for files outside your home directory.

Run nautilus again from terminal and then navigate to **/usr/share/applications**
and right click on Files > properties > permissions 
Does it show owned by root as in pic.

---

### Post by michael_hansen2 on 2014-09-07
echo output:
My user name

Permissions on /usr/share/applications/file:
All root as your screenshot

---

### Post by michael_hansen2 on 2014-09-07
I'll try this (by "this" i mean the other tip that " mc4man" suggested") shortly. I cannot log out right now as I'm running some processes of VirtualBox that needs to finish.

---

### Post by steeldriver on 2014-09-07
Is it actually running ***as root*** - or is it opening the filesystem root directory / instead of your home directory? what is the result of the command

```

ps -ef | grep [n]autilus

```

---

### Post by michael_hansen2 on 2014-09-08
> **steeldriver said:**
> Is it actually running ***as root*** - or is it opening the filesystem root directory / instead of your home directory? what is the result of the command

```

ps -ef | grep [n]autilus

```

Output is:
michael   7204  6826  1 09:59 ?        00:00:10 nautilus -n

This looks a bit odd, unless I'm reading it incorrect. It does look like it opens it as my user. I don't think it does though. It doesn't just open in the root folder. It opens in the folder I want it to, but in the title (Top) it says "Nautilus Root" and in the unity bar on the left  the icon is a big "?" and it says "Nautilus Root" there as well.

---

### Post by michael_hansen2 on 2014-09-08
> **mc4man said:**
> Maybe try this - 
```
cp /usr/share/applications/nautilus.desktop ~/.local/share/applications/
```
Then log out/in
Once logged back in go - 
alt+F2 > gtk-launch nautilus

If it open normally then right click on the unity launcher icon > lock to launcher

If it doesn't then 
gedit ~/.local/share/applications/nautilus.desktop 
and post

I tried this and it didn't work so here's the output:

[Desktop Entry]
Name=Files
Comment=Access and organize files
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window %U
Icon=system-file-manager
Terminal=false
Type=Application
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;FileManager;
MimeType=inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.10.1
X-GNOME-UsesNotifications=true
Actions=Window;
X-Unity-IconBackgroundColor=#af4853
X-Ubuntu-Gettext-Domain=nautilus

[Desktop Action Window]
Name=Open a New Window
Exec=nautilus --new-window
OnlyShowIn=Unity;

---

### Post by deadflowr on 2014-09-08
well a quick test to see if you are really running as root, versus just some weird output, would be to navigate to a restricted folder/file.
I would go to "Computer" in the side pane click on it and look at the directory Root. If it looks like the rest you might be running as root. But if you see an X in the corner, then you are not running as root.

---

### Post by michael_hansen2 on 2014-09-08
> **deadflowr said:**
> well a quick test to see if you are really running as root, versus just some weird output, would be to navigate to a restricted folder/file.
I would go to "Computer" in the side pane click on it and look at the directory Root. If it looks like the rest you might be running as root. But if you see an X in the corner, then you are not running as root.

I tried this and I could NOT go to the restricted folder so I'm not really running as root it appears...its just a weird output then. Any ideas how to fix it still?

---

### Post by mc4man on 2014-09-08
> **michael_hansen2 said:**
> I tried this and I could NOT go to the restricted folder so I'm not really running as root it appears...its just a weird output then. Any ideas how to fix it still?
Well you've never said what "a weird output" is...

(- for future info - in Ubuntu a root nautilus window will always have a menu bar in the nautilus window so it's easy to tell if it's open as root..

---

### Post by michael_hansen2 on 2014-09-08
> **mc4man said:**
> Well you've never said what "a weird output" is...

(- for future info - in Ubuntu a root nautilus window will always have a menu bar in the nautilus window so it's easy to tell if it's open as root..

Regarding 'weird output' then I just responded to deadflowr. He used  that term so I used his exact term to make it easier to follow for other  readers. I assumed by "weird output" that he just meant that the  nautilus header was showing "Root Nautilus" even though it wasn't  actually root. 

What do you mean by this: "(- for future info -  in Ubuntu a root nautilus window will always have a  menu bar in the nautilus window so it's easy to tell if it's open as  root.."?. When I run nautilus via root (gksudo nautilus) is says  "Nautilus Root" in the top menu. It does this if I don't run it as root as well. Both  ways also has the "?" as an icon in the left unity bar. 

Any ideas  how to resolve it? It might not be root as it sounded like but its  still pretty annoying. Would love a fix to it as I've tried everything I  could think off.

---

### Post by michael_hansen2 on 2014-09-08
Not sure if this helps or makes it worse, but here's another finding. 

I run nautilus by clicking a folder on my desktop. It says "Nautilus Root" yet I can not access any "root only folders (As expected). I then click "Lock to launcher" in the unity bar. I close the window and then when I click the newly created  nautilus shortcut on unity the root password dialog pops up. If I enter my admin/root password I can now access root only folders which I could not before. Very odd.

---

### Post by CantankRus on 2014-09-08
After doing what mc4man said in [**_[COLOR="#B22222"]post #10[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2243118&p=13117381#post13117381") you should have a **nautilus.desktop** file in **~/.local/share/applications**
Open a terminal and run...
```
nautilus ~/.local/share/applications
```
and drag and drop the **nautilus.desktop** file to the launcher.
How does that behave?

---

### Post by steeldriver on 2014-09-08
It sounds like you've created a launcher on your desktop that was intended to (but actually doesn't) start a nautilus session as root

---

### Post by michael_hansen2 on 2014-09-08
> **CantankRus said:**
> After doing what mc4man said in [**_[COLOR=#B22222]post #10[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2243118&p=13117381#post13117381") you should have a **nautilus.desktop** file in **~/.local/share/applications**
Open a terminal and run...
```
nautilus ~/.local/share/applications
```
and drag and drop the **nautilus.desktop** file to the launcher.
How does that behave?

Now this worked. Sweet. When I start Nautilus from this new shortcut it does not open with "Nautilus Root" in the title. Even more awesome (But kinda weird), when I now open a folder shortcut on my desktop it no longer opens as with "Nautilus Root". Awesome! Thanks for the help guys.

---

### Post by michael_hansen2 on 2014-09-08
> **steeldriver said:**
> It sounds like you've created a launcher on your desktop that was intended to (but actually doesn't) start a nautilus session as root

Yeah, maybe. I have a shortcut for root access, but this issue impacted all folder shortcuts as well as running it from the unity search bar. I'm guessing I had a broken nautilus.desktop in the application folder, but I'm just guessing. I really don't get this...just happy that it works now :)

---

### Post by mc4man on 2014-09-08
What nautilus shows in the title bar corresponds to the folder that it's open on. 
What it shows in the unity panel  corresponds to the Name= line in the .desktop that it's launched from. So in 14.04 it would be Name=Files so it would show "Files"
What ever you were doing before likely was using a .desktop where that line was Name=Nautilus Root

When you run gtk-launch <appname> then the app will be started from the first available .desktop for that app, pecking order would be 
~/.local/share/applications
/usr/local/share/applications
/usr/share/applications

As far as what I meant before about an actual root nautilus window see screen, there is a menu bar as a root nautilus browser window does not support global menus

---

### Post by CantankRus on 2014-09-08
> **michael_hansen2 said:**
> Yeah, maybe. I have a shortcut for root access, but this issue impacted all folder shortcuts as well as running it from the unity search bar. I'm guessing I had a broken nautilus.desktop in the application folder, but I'm just guessing. I really don't get this...just happy that it works now :)
Good to see fixed. :KS

A nautilus.desktop file created in **~/.local/share/applications** will override .desktop launchers in **/usr/share/applications**

Another confusing aspect is .desktop files show as their name configured in the .desktop when viewed in **/usr/share/applications**
and to view the .desktop file you need to drag and drop it in a gedit window.

---

