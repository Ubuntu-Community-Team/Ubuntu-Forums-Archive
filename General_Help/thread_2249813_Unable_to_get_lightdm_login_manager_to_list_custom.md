---
title: "Unable to get lightdm login manager to list custom xsession at login prompt"
date: 2014-10-24
forum: General Help
---

### Post by myacct on 2014-10-24
[FONT=Calibri]Hello, [/FONT] 
 

 [FONT=Calibri]I'm trying to create a new xsession containing Unity's top panel but not the main panel.  I believe that I configured the .session and .desktop files correctly but am unable to get the login manager (lightdm) to display the option to select the new session at login.  Any help will be much appreciated, thank you.[/FONT]

 

 [FONT=Calibri]Here's what I did:[/FONT]
 

 [FONT=Calibri](1) I created a new file named “custom-unity2d.desktop” in /usr/share/xsession/ with the following contents:[/FONT]
 

 [FONT=Calibri][Desktop Entry] [/FONT]
 [FONT=Calibri]Name=Custom Unity2D [/FONT]
 [FONT=Calibri]Exec=gnome-session --session=custom-unity2d [/FONT]
 [FONT=Calibri]TryExec=custom-unity2d.session [/FONT]
 [FONT=Calibri]Icon= [/FONT]
 [FONT=Calibri]Type=Application [/FONT]
 [FONT=Calibri]X-Ubuntu-Gettext-Domain=gnome-session-3.0 [/FONT]
   
 

 [FONT=Calibri](2) I created a new file named “custom-unity2d.session” in /usr/share/gnome-session/sessions/ with the following contents:[/FONT]
 

 [FONT=Calibri][GNOME Session] [/FONT]
 [FONT=Calibri]Name=Custom Unity2D Session [/FONT]
 [FONT=Calibri]RequiredComponents=gnome-settings-daemon; [/FONT]
 [FONT=Calibri]RequiredProviders=windowmanager;panel; [/FONT]
 [FONT=Calibri]DefaultProvider-windowmanager=metacity [/FONT]
 [FONT=Calibri]DefaultProvider-panel=unity-2d-panel [/FONT]
 [FONT=Calibri]FallbackSession=ubuntu-2d [/FONT]
 [FONT=Calibri]DesktopName=GNOME[/FONT]
 

 [FONT=Calibri](3) I logged out expecting that when the lightdm login manager appeared I would have the option to select “custom-unity2d” but it isn't there....[/FONT]

 

 [FONT=Calibri](Note) I also created a .Xsession directory in my home directory  and placed custom-unity2d.desktop file there but that didn't solve the problem.
[/FONT]
[FONT=Calibri]Thank again[/FONT]

---

