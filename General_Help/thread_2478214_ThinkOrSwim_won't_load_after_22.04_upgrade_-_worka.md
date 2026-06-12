---
title: "ThinkOrSwim won't load after 22.04 upgrade - workaround"
date: 2022-08-19
forum: General Help
---

### Post by lpmurphy on 2022-08-19
After upgrading to 22.04 TDA's TOS would load once correctly then would not display a working page subsequent attempts to run the program.   1st run, TOS does not have a "workspace.20_xxxx.tos.prod.xml" file in Home/thinkorswim.  It saves this file when the app is closed.  This file saves your settings for gadgets and colored links.  In order to workaround this problem:
1 - Delete (or rename to preserve current settings) the 'workspace.20_xxxxxxx.tos.prod.xml' file.  Then TOS will start successfully.
2 - ** Once running with the default gadget customization.  If desired, setup your screens then save them by clicking Setup/Save workspace as.
3.  You will have to delete the workspace file that TOS will create each time you exit the program so TOS will start up again.

** Intermittently I have been able to click on Setup/mybackupfilename and get my saved customized screens to load.  Most times it blanks out TOS and does not work.

I tried reinstalling TOS and ZULU OpenJDK 11, it did not help.  Don't bother with Zulu OpenJDK 17, does not work at all.

---

### Post by michael-enquist on 2022-08-31
I have been having the same problem.

Through circumstances, I ended up reinstalling Ubuntu 20.04 and, during the installation process, it upgraded to 22.04.
I installed TOS using the method described on the how2shout.com page: How to install Thinkorswim on Ubuntu 20.04 LTS Linux
At the end of the installation, I started TOS. It ran normally. 
When I quit TOS, there was no desktop icon, so I tried creating the "Thinkorswim.desktop" program as described in the page above.
When I run that file as a program, I get a pup-up that says:

     thinkorswim has encountered a critical error and cannot be started.Please click Download and reinstall the application.

When I click "Download," I just get another copy of the thinkorswim_installer.sh file.
I install it again, and launch TOS at the end.

Now TOS is running, but there is no screen.
When I press the TOS logo in the sidebar, it says java-lang-Thread in the top row.
When I hit the Super Key, it shows a clear window with the TOS logo at the bottom. Hovering over that window shows "Paper@thinkorswim [build 1975]"
And, when looking at that window via the Super Key, when I hit the (x), I get the usual "Confirm Logoff?" window.
I do not see any file starting with the name "workspace.20..."
The only file starting with "workspace." is one called 

workspace.jykqqfjyw56unsg.tos.demo.xml

There are three copies of that file. One in /usr/local/thinkorswim/. one in /opt/thinkorswim/ and one in /opt/thinkorswim/backup/

I rename that file in all three locations.

I tried to run TOS from the command line by typing sudo /opt/thinkorswim/./thinkorswim, but that resulted in the same problem the program running, but now workspace.
I tried again using sudo usr/local/thinkorswim/./local and TOS opened correclty.

I edited the Thinkorswim.desktop file, but running that as a program still gets the message above.

Below is the Thinkorswim.desktop file.

I guess we just have to keep deleting or renaming the workspace. files?

Thanks,

ME


**************

Thinkorswim.desktop

[Desktop Entry]
Version 1.0
Type=Application
Name=Thinkorswim
Comment=Trading
Exec=sudo /usr/local/thinkorswim/./thinkorswim
Icon=/opt/thinkorswim/thinklogo.png
Terminal=true
StartupNotify=false

---

