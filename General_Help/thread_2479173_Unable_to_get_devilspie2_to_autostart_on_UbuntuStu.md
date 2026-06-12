---
title: "Unable to get devilspie2 to autostart on UbuntuStudio 22.04.1 LTS"
date: 2022-09-16
forum: General Help
---

### Post by Nosphky on 2022-09-16
I've just made a fresh install of 22.04.1 and am having to work through a load of strangeness with KDE plasma whereas I've been used to Xfce for many years but I'm sure I'll get there sooner or later. My first problem that I haven't managed to crack is to get devilspie2 to autostart (it was easy enough in 20.04 LTS).

When adding the application in Autostart, if I just put  'devilspie2', when I restart the computer and check the running processes, devilspie2 is not running. I can open a terminal (Konsole) and just type 'devilspie2' and it starts or better still type in 'nohup devilspie2 &' and it starts and I can close the terminal window.

I've tried using 'nohup devilspie2 &' as the command in Autostart and that does start the devilspie2 process but leaves me with an open Konsole window. If I then close that Konsole, the devilspie2 process gets killed.

So at the moment, my workaround is to boot up, then run 'nohup devilspie2 &' in a Konsole terminal before running my other applications. Clearly, I must be missing something and I'm hoping someone can help me out.

---

### Post by #&amp;thj^% on 2022-09-16
To set up automatic startup through the terminal on KDE Plasma 5, you must first move the command-line session from the home folder (~) to /usr/share/applications/, as this is where Linux keeps all program shortcuts.
```

cd /usr/share/applications/
```

Using the ls command, list all of the items in the /usr/share/applications directory.
```

ls
```

Or, if you&#8217;re having trouble sorting through the huge list of shortcut files, try:
```

ls | grep 'programname'
```

After you&#8217;ve found the name of the program, take it and plug it into the CP command below to create a new startup entry.
```

mkdir -p ~/.config/autostart/

cp programname.desktop ~/.config/autostart/
```

Update the file&#8217;s permissions to ensure that KDE will handle the app shortcut correctly.
```

sudo chmod +x ~/.config/autostart/programname.desktop
```

Repeat this process as many times as you&#8217;d like to create startup entries for KDE.
Let us know, this works for me, I don't use  devilspie2 though so I'm curious if this works for you.

---

### Post by Nosphky on 2022-09-16
Hi 1fallen: thanks for the reply.  The problem is that there is no entry for devilspie2.desktop  in /usr/share/applications/.  So I get stuck at that point.

I installed devilspie2 through the Muon package manager and  'which devilspie2' shows that it's installed in   /usr/bin/devilspie2

How does the .desktop file get created?

---

### Post by #&amp;thj^% on 2022-09-16
> **Nosphky said:**
> 
How does the .desktop file get created?
If easier you can also create a systemd service, but have a look at this: [https://bbs.archlinux.org/viewtopic.php?id=192017](https://bbs.archlinux.org/viewtopic.php?id=192017)
If your still unsuccessful I'll have a look at it installed on my system tomorrow.

---

### Post by Nosphky on 2022-09-16
> **1fallen said:**
> If easier you can also create a systemd service, but have a look at this: [https://bbs.archlinux.org/viewtopic.php?id=192017](https://bbs.archlinux.org/viewtopic.php?id=192017)
If your still unsuccessful I'll have a look at it installed on my system tomorrow.

I've been to and read through that post, thanks, but I'm afraid it's not clear enough for me to write a devilspie2.service file. The #7 and final post in the thread says 'This will do it ...' but it doesn't look like a .services file to me especially when the first line is a mkdir command.

If devilspie2 is run as a systemd service, will it still pick up the config data in my .config/devilspie2  files ?

---

### Post by #&amp;thj^% on 2022-09-16
> **Nosphky said:**
> I've been to and read through that post, thanks, but I'm afraid it's not clear enough for me to write a devilspie2.service file. The #7 and final post in the thread says 'This will do it ...' but it doesn't look like a .services file to me especially when the first line is a mkdir command.

If devilspie2 is run as a systemd service, will it still pick up the config data in my .config/devilspie2  files ?

Yep IE:
```
devilspie2 --debug
Running devilspie2 in debug mode.

Using scripts from folder: /home/me/.config/devilspie2
------------
List of Lua files handling "window_open" events in folder:
/home/me/.config/devilspie2/debug.lua
List of Lua files handling "window_close" events in folder:
List of Lua files handling "window_focus" events in folder:
List of Lua files handling "window_blur" events in folder:
------------
Application: Xfce Terminal
Window: Terminal - 
Application: Thunar
Window: devilspie2
Application: xed
Window: *Unsaved Document 1
Application: Xfce Terminal
Window: Terminal - 
Application: pavucontrol
Window: Volume Control
Application: strawberry
Window: James Gang - Funk #49
Application: Firefox
Window: Tutorial – Devilspie2 » Linux Magazine — Mozilla Firefox
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: xfdesktop
Window: Desktop
Application: xfce4-panel
Window: xfce4-panel
Application: xfce4-panel
Window: xfce4-panel
Application: xfce4-panel
Window: xfce4-panel

```
 As you can see I'm not on KDE Plasma ATM

---

### Post by Nosphky on 2022-09-16
While navigating to have a quick look at my .config/devilspie2 lua files, I found  a devilspie2.desktop file in my /.config/autostart/ directory. It had been created by the gui Autostart in System settings which I had used in my vain attempts to get devilspie2 autostarted.

I had a look at that .desktop file and deleted the stuff about using a terminal and added the path /usr/bin/devilspie2 .

Then I rebooted and devilspie2 process was running and when I started my applications they loaded in the correct desktops.  So it looks like the problem is solved.

Thanks for your help without which I wouldn't have found that .desktop file.

---

### Post by Holger_Gehrke on 2022-09-16
> **Nosphky said:**
> How does the .desktop file get created?

Quite simple. You write it. It's just a simple text file, you have lots of examples in /usr/share/applications. If you like reading through specs instead, you can find the documentation for desktop files at [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/) .

Holger

---

### Post by Nosphky on 2022-09-16
Thanks Holger_Gehke, as you see above, I just found and modified the .desktop file which was originally created by the GUI in System Settings. I hadn't come across them before and I'll be pleased to read that documentation you referenced.

---

### Post by vanadium on 2022-09-17
Introduce some delay in starting devilspie: preceed the command with a sleep command: "sh -c "sleep 8 && devilspie2" (for me, I found I need a full 8 seconds)

---

### Post by Nosphky on 2022-09-17
Thanks, vanadium, for that idea. But after booting up today, I can confirm that the little edit I made to the devilspie2.desktop file does work and after boot, the devilspie2 process is running and operating as I was used to seeing in UbuntuStudio 20.04 LTS. My problem was basically ignorance of the existence of .desktop files and made worse by being unable to specify the path to devilspie2 in the  System Settings Autostart GUI (at least I didn't see how to enter the path).

---

