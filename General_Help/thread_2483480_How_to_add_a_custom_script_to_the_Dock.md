---
title: "How to add a custom script to the Dock"
date: 2023-01-31
forum: General Help
---

### Post by cforput on 2023-01-31
I have 3 or 4 scripts that I want to add as icons on my dock. I've been searching all morning on how to do that and have come up blank. Obviously I'm just searching wrong. 

Examples

.sh or .desktop file that has "shutdown now()"
.sh or .desktop file that has "firefox custom.html file in my home directory"
.sh or .desktop file that has "restart"

I've tried making executable .desktop files and putting them in my .local/share/applications folder but don't know how to create a new Dock entry to run them.

Let's not worry about the syntax of the scripts themselves. If I run them at the command line, they do what I want. I just need directions on how to put them on the dock.

---

### Post by monkeybrain20122 on 2023-01-31
Do the .desktop files launch the scripts if you click on them? What is your DE? I think Nautilus doesn't allow scripts to be run from $HOME a few iterations ago. Maybe try to move the .desktop files to /usr/local/share/applications or maybe use a different file manager as default like nemo.

---

### Post by MAFoElffen on 2023-01-31
> **monkeybrain20122 said:**
> Do the .desktop files launch the scripts if you click on them? What is your DE? I think Nautilus doesn't allow scripts to be run from $HOME a few iterations ago.
When the Lunar repo's opened up, someone told me that and I decided to test that. I was able to add a working desktop item to start a script. And I was able to start scripts from within $HOME with Nautilus. So I(because of that) 'm not sure that is sometimes or always true.
 > **monkeybrain20122 said:**
> Maybe try to move the .desktop files to /usr/local/share/applications or maybe use a different file manager as default like nemo.
+1. What I was thinking for this...

---

### Post by deadflowr on 2023-01-31
> I've tried making executable .desktop files and putting them in my .local/share/applications folder but don't know how to create a new Dock entry to run them.

If you created the desktop file properly then it should have a Name entry which you can search for in the Activities overview and then right click add to favorites which will place it on the dock.
Or am I missing something?

This link is older but the basics are the same on how to create a proper .desktop file: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
Or have gotten beyond that part successfully?

---

### Post by monkeybrain20122 on 2023-01-31
> **MAFoElffen said:**
> 
When the Lunar repo's opened up, someone told me that and I decided to test that. I was able to add a working desktop item to start a script. And I was able to start scripts from within $HOME with Nautilus. So I(because of that) 'm not sure that is sometimes or always true.
 

It wasn't true before but I think the ability to run executables from $HOME was removed at one point. I remember reading threads that people couldn't start their appimages by clicking on them and the explanation was Nautilus no longer allowed it. I have stopped using nautilus since a few years ago (actually I don't use gnome shell except on VMs even there I replace nautilus with nemo). Among other things it is ridiculous that you have to make a template in order to have the basic function of creating an empty document by right clicking. It is just pita to use.

---

### Post by dragonfly41 on 2023-01-31
I use Actiona for extensive UI automation. It is in the repo.
Actiona session shows in Dock.
Inside the Actiona container you can access many Qt5 objects from running commands to launching apps.

---

### Post by MAFoElffen on 2023-01-31
I did this on my Lunar daily build tests today...

Create your .desktop file in /usr/share/applications/ directory... In launcher applications, find your desktop file... I set an Icon I could find easily... Right-click and select save to favorites. Will be saved/added to the Dock.

Here was my system-info.desktop file:
```

[Desktop Entry]
Type=Application
Terminal=true
Name=system-info
Icon=/usr/share/ibus-table/icons/acommit.svg
Exec=/home/mafoelffen/Scripts/system-info

```
One tip I found for writing scripts to work from a launcher, is that if you want the user to see something before it disappears (closes the terminal), that I add a pause type of statement at the end, so the user can hit a key before closing the terminal window.

---

### Post by cforput on 2023-02-01
Ubuntu 22.04 fresh install

I put my .desktop files in ~/.local/share/applications so it's just for me. For some reason it takes 10 to 15 minutes for them to show up when I search, but they eventually do show, so I'm going to mark as solved. Thanks everyone.

---

### Post by mIk3_08 on 2023-02-01
> **cforput said:**
>  so I'm going to mark as solved. Thanks everyone.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

