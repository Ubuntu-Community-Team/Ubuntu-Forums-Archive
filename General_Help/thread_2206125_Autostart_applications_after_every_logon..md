---
title: "Autostart applications after every logon."
date: 2014-02-17
forum: General Help
---

### Post by gaseabra on 2014-02-17
Hi guys,

I'm having a session issue and I'll try to explain it here. Everytime I log in to my users, tons of applications I've previoulsy used are starting automatically like Google Chrome, Skype, gedit, Mozilla Thinderbird. I haven't set all of those to autostart with my session and I have no clue why they are starting automatically. 

Can somebody help me with that?

Cheers,

---

### Post by gaseabra on 2014-02-17
> **gaseabra said:**
> Hi guys,

I'm having a session issue and I'll try to explain it here. Everytime I log in to my users, tons of applications I've previoulsy used are starting automatically like Google Chrome, Skype, gedit, Mozilla Thinderbird. I haven't set all of those to autostart with my session and I have no clue why they are starting automatically. 

Can somebody help me with that?

Cheers,


By the way, I have Xubuntu 12.04.

---

### Post by Toz on 2014-02-17
When you logout, you have an option to "Save session for future logins". Make sure this is unchecked.
Having said that, there is an issue with Xfce sometimes saving sessions when its not supposed to.
To manually clear out your saved sessions cache (assuming that you are running the default Xfce 4.8 that was shipped with Xubuntu 12.04), before you log in:
1. Go to the first tty (Ctrl+Alt+F1)
2. Log in to the text console
3. Issue these commands to clear the sessions cache:
```
cd .cache
rm -rf sessions
```
4. Go back to the gui login screen (Ctrl+Alt+F7)
5. Log in and see if it worked.

---

### Post by gaseabra on 2014-02-18
> **Toz said:**
> When you logout, you have an option to "Save session for future logins". Make sure this is unchecked.
Having said that, there is an issue with Xfce sometimes saving sessions when its not supposed to.
To manually clear out your saved sessions cache (assuming that you are running the default Xfce 4.8 that was shipped with Xubuntu 12.04), before you log in:
1. Go to the first tty (Ctrl+Alt+F1)
2. Log in to the text console
3. Issue these commands to clear the sessions cache:
```
cd .cache
rm -rf sessions
```
4. Go back to the gui login screen (Ctrl+Alt+F7)
5. Log in and see if it worked.

Thank you for the response. 

Sadly, it didn't work. The "Save session..." option is uncked. I ran the commands, restarted the computer, but everything keeps loading just like before :(

---

### Post by Toz on 2014-02-18
Can you post back the results of:
```
ls ~/.config/autostart/
```
...and
```
ls -l ~/.cache/sessions
```

---

### Post by gaseabra on 2014-02-18
ls ~/.config/autostart/:
xfce4-settings-helper-autostart.desktop

ls -l ~/.cache/sessions:
File or directory not found.

---

### Post by Toz on 2014-02-18
Was this a straight Xubuntu install? Did you install and use any other environments (kde, unity, lxde, etc...)?

Try this command. It will display all instances of "gedit" in your home directory:
```
fgrep -ri gedit ~
```
...lets see where it exists. It might take a while to run and may return a lot of results.

---

### Post by Bucky Ball on 2014-02-18
Boot, when at a desktop close everything so you have an empty desktop as you'd like it when you boot, restart the computer, but in the Logout GUI where you select to log out, restart, shutdown, etc., check the tick box that says 'Save Session'. Restart.

You should now be taken to the system exactly as you left it when you restarted. My guess is that this option was inadvertantly ticked at one time or the other.

Next time you shutdown, make sure that box is UNticked. ;)

---

### Post by monkeybrain20122 on 2014-02-18
I have experienced this annoying behaviour on xfce for as long as I can remember (xubuntu 10.xx and the latest manjaro) The only sure fire way to fix it seems to be simply lock the file ~/.cache/session. Right click and change permission to none, then reboot.

---

### Post by gaseabra on 2014-02-19
fgrep -ri gedit ~
/root/.bash_history:apt-get install krusader skype thunderbird chromium-browser brasero vlc banshee gimp pinta libreoffice gedit aptitude
/root/.bash_history:gedit ~/.config/chromium/Default/Preferences
/root/.bash_history:gedit /etc/apt/sources.list
/root/.bash_history:sudo gedit /etc/default/apport
/root/.config/gedit/accels:; gedit GtkAccelMap rc-file         -*- scheme -*-
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditCut" "<Primary>x")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/File" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Tools" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsNextDocument" "<Primary><Alt>Page_Down")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditDelete" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowPanelsActions/ViewSidePanel" "F9")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/View" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindPrevious" "<Primary><Shift>g")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsPreviousTabGroup" "<Primary><Shift><Alt>Page_Up")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrint" "<Primary>p")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewToolbar" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpContents" "F1")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditRedo" "<Primary><Shift>z")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Search" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Edit" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditSpellPluginActions/CheckSpell" "<Shift>F7")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpAbout" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FileCloseAll" "<Primary><Shift>w")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsMoveToNewWindow" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFind" "<Primary>f")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FileSave" "<Primary>s")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditQuitWindowActions/FileQuit" "<Primary>q")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewStatusbar" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditSpellPluginActions/ConfigSpell" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileOpen" "<Primary>o")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/ViewHighlightMode" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchGoToLine" "<Primary>i")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchReplace" "<Primary>h")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAs" "<Primary><Shift>s")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchClearHighlight" "<Primary><Shift>k")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrintPreview" "<Primary><Shift>p")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditTimePluginActions/InsertDateAndTime" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditUndo" "<Primary>z")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditCloseWindowActions/FileClose" "<Primary>w")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditSpellPluginActions/AutoSpell" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditPaste" "<Primary>v")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAll" "<Primary><Shift>l")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindNext" "<Primary>g")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowPanelsActions/ViewBottomPanel" "<Primary>F9")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsNextTabGroup" "<Primary><Shift><Alt>Page_Down")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewFullscreen" "F11")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditCopy" "<Primary>c")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/FileRevert" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileNew" "<Primary>n")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Documents" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsPreviousDocument" "<Primary><Alt>Page_Up")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsNewTabGroup" "<Primary><Alt>n")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditDocinfoPluginActions/DocumentStatistics" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/EditPreferences" "")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowActions/EditSelectAll" "<Primary>a")
/root/.config/gedit/accels:; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Help" "")
Arquivo binário /root/.config/dconf/user coincide com o padrão
/root/.local/share/recently-used.xbel:          <bookmark:group>gedit</bookmark:group>
/root/.local/share/recently-used.xbel:          <bookmark:application name="gedit" exec="&apos;gedit %u&apos;" modified="2013-04-30T12:41:35Z" count="2"/>
Arquivo binário /root/.local/share/zeitgeist/activity.sqlite-wal coincide com o padrão
Arquivo binário /root/.local/share/zeitgeist/fts.index/postlist.DB coincide com o padrão

---

### Post by Toz on 2014-02-19
Are you logged in as root or did you run the command in a window with root privileges?

---

### Post by gaseabra on 2014-02-19
> **Toz said:**
> Are you logged in as root or did you run the command in a window with root privileges?

I'm looged in as root.

---

### Post by gaseabra on 2014-02-19
Thanks for the response, but I'm sorry to inform you it didn't work.

---

### Post by Toz on 2014-02-19
Whats in your system-wide autostart directories?
```
ls -l /etc/xdg/autostart
```
```
ls -l /etc/xdg/xdg-xubuntu/autostart
```

---

### Post by gaseabra on 2014-02-19
```
ls -l /etc/xdg/autostart
total 112
-rw-r--r-- 1 root root  306 Mai 17  2012 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  209 Abr 18  2012 blueman.desktop
-rw-r--r-- 1 root root  451 Abr 12  2012 gnome-keyring-gpg.desktop
-rw-r--r-- 1 root root  479 Abr 12  2012 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root  472 Abr 12  2012 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root  454 Abr 12  2012 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root  279 Mar 23  2012 gsettings-data-convert.desktop
-rw-r--r-- 1 root root  304 Mar  8  2013 hplip-systray.desktop
-rw-r--r-- 1 root root  304 Mar  8  2013 hplip-systray.desktop.dpkg-old
-rw-r--r-- 1 root root  372 Abr 12  2012 jockey-gtk.desktop
-rw-r--r-- 1 root root  210 Out 18  2012 nautilus-autostart.desktop
-rw-r--r-- 1 root root  342 Abr  3  2012 nm-applet.desktop
-rw-r--r-- 1 root root  244 Mar 27  2012 onboard-autostart.desktop
-rw-r--r-- 1 root root  358 Fev 11  2012 polkit-gnome-authentication-agent-1.desktop
-rw-r--r-- 1 root root  391 Mar 29  2012 print-applet.desktop
-rw-r--r-- 1 root root  259 Jul 19  2012 psensor.desktop
-rw-r--r-- 1 root root 3920 Abr 12  2012 pulseaudio.desktop
-rw-r--r-- 1 root root  256 Abr 12  2012 pulseaudio-kde.desktop
-rw-r--r-- 1 root root 8937 Abr 20  2012 update-notifier.desktop
-rw-r--r-- 1 root root  312 Abr  4  2012 user-dirs-update-gtk.desktop
-rw-r--r-- 1 root root 2434 Jun 25  2011 xfce4-notes-autostart.desktop
-rw-r--r-- 1 root root 4199 Abr  8  2012 xfce4-power-manager.desktop
-rw-r--r-- 1 root root  150 Mar 13  2012 xfce4-settings-helper-autostart.desktop
-rw-r--r-- 1 root root  357 Mar 21  2012 xfce4-volumed.desktop
-rw-r--r-- 1 root root  336 Abr 11  2012 zeitgeist-datahub.desktop
```

```
ls -l /etc/xdg/xdg-xubuntu/autostart
total 4
-rw-r--r-- 1 root root 29 Abr  4  2010 xfce4-tips-autostart.desktop
```

---

### Post by Bucky Ball on 2014-02-19
Please use [code] tags when posting output from the terminal. Much neater and easier to read. Thanks. I've added them to your last post so you can see where they go. You can use 'Adv. Reply' or 'Go Advanced' and use the # icon or do them manually.

---

### Post by gaseabra on 2014-02-19
> **Bucky Ball said:**
> Please use [code] tags when posting output from the terminal. Much neater and easier to read. Thanks. I've added them to your last post so you can see where they go. You can use 'Adv. Reply' or 'Go Advanced' and use the # icon or do them manually.

Thank you and sorry for that.

---

### Post by pqwoerituytrueiwoq on 2014-02-19
i have had this issue, in "Session and Startup" in the "Session" tab set the "Restart Style" to "Never"
i always have issues with this feature conflicting with my startup applications so i have 2 instances of stuff like cario dock running, for esveral startup apps i made them run a custom command that runs it though a script that checks if the app is running before starting it

---

### Post by gaseabra on 2014-02-19
It worked for most of the applications, but I still have skype and google chrome starting automatically.

---

### Post by monkeybrain20122 on 2014-02-19
> **pqwoerituytrueiwoq said:**
> i have had this issue, in "Session and Startup" in the "Session" tab set the "Restart Style" to "Never"
i always have issues with this feature conflicting with my startup applications so i have 2 instances of stuff like cario dock running, for esveral startup apps i made them run a custom command that runs it though a script that checks if the app is running before starting it

Exactly the same thing with cairo dock. Locking  ~/.cache/session fixed it.

---

### Post by monkeybrain20122 on 2014-02-19
> **gaseabra said:**
> I'm looged in as root.

Why???

---

### Post by gaseabra on 2014-02-19
> **monkeybrain20122 said:**
> Why???


I always do. It's practical.

---

### Post by gaseabra on 2014-02-19
> **Toz said:**
> When you logout, you have an option to "Save session for future logins". Make sure this is unchecked.
Having said that, there is an issue with Xfce sometimes saving sessions when its not supposed to.
To manually clear out your saved sessions cache (assuming that you are running the default Xfce 4.8 that was shipped with Xubuntu 12.04), before you log in:
1. Go to the first tty (Ctrl+Alt+F1)
2. Log in to the text console
3. Issue these commands to clear the sessions cache:
```
cd .cache
rm -rf sessions
```
4. Go back to the gui login screen (Ctrl+Alt+F7)
5. Log in and see if it worked.

I did that again and suddenly it worked. I have no apps autostarting.

Thanks all of you guys!

---

### Post by monkeybrain20122 on 2014-02-19
> **gaseabra said:**
> I always do. It's practical.

It is very bad for security.There is a reason why Ubuntu disables root by default.

---

### Post by Bucky Ball on 2014-02-19
Yes, unwise running as root for a range of reasons. Please mark this thread as solved to help others by following the instructions in my signature. Thanks.

---

