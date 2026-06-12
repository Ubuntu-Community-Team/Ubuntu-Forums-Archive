---
title: "Authorisation failure - Muon - and other apps requiring elevated permissions"
date: 2015-02-10
forum: General Help
---

### Post by timgood on 2015-02-10
I'm running Kubuntu 14.10 64bit. Following some updates yesterday I am faced with this behaviour:

1. Muon Update will find updates but will not install them. It does not ask for a password but simply gives the message "This operation cannot continue since proper authorization was not provided". I can upgrade via terminal only.

2. Shutdown, reboot and logout buttons no longer work. I have to do this via terminal.

3. Ubuntu Tweak will launch but will not run any options to clean the cache, uninstall old kernels etc. Does not ask for authorisation, simply sits there looking pretty.

4. Muon Discover will not allow the installation of any software packages, giving the same error message as Muon Update.

I've searched the usual sources and tried various fixes, including checking that polkit-kde-1 is installed (it is) and reconfiguring PAM, but after rebooting and logging in and out the problem persists. Large quantities of virtual beer and kudos to anyone who can help me sort this annoyance.

Thanks guys!

---

### Post by ajgreeny on 2015-02-10
If you are starting the muon apps from the menu system, can you find out in some way what command the entries for the muon applications is actually using.

If you go to a terminal with root permissions using **sudo -i** then run muon with the appropriate command, can you update that way?

If so, it points to a failure either of the menu system itself, or the command it is using to open muon.

---

### Post by timgood on 2015-02-10
OK I have now fixed this - I hope. I noticed that some apps that used to run in the system tray were also not running and not starting on boot (things like kup, shutter and mailnag for example). I booted into a terminal, logged on and started x manually. All my system tray icons came back, and Muon asked for authorisation (which as I was logged in from a terminal, didn't work). But following a reboot, the system is now working normally. Why? I have no idea. I hope it stays like this! 

ajgreeny:- yes, I could update if I ran Muon as root. Must have been something to do with PAM, but as I say, I have no clue as to why it stopped working or why after I logged in from terminal and started x it repaired itself. :(

I will mark this as solved in the hope that my boundless optimism will please the KDEKarma daemons.

---

### Post by ruth4 on 2015-08-18
> **timgood said:**
> OK I have now fixed this - I hope. I noticed that some apps that used to run in the system tray were also not running and not starting on boot (things like kup, shutter and mailnag for example). I booted into a terminal, logged on and started x manually. All my system tray icons came back, and Muon asked for authorisation (which as I was logged in from a terminal, didn't work). But following a reboot, the system is now working normally. Why? I have no idea. I hope it stays like this! 

ajgreeny:- yes, I could update if I ran Muon as root. Must have been something to do with PAM, but as I say, I have no clue as to why it stopped working or why after I logged in from terminal and started x it repaired itself. :(

I will mark this as solved in the hope that my boundless optimism will please the KDEKarma daemons.


I have the same problem and got solved with: sudo apt-get update && upgrade

---

### Post by Peter_Schmidt on 2015-11-27
I had a similar problem after upgrading Kubuntu (Muon being unable to install updates and KDE menu and shortcuts for shutdown not working). My issue was resolved by removing ```
.kde/share/config/ksmserverrc
``` as suggested in this thread: [https://www.kubuntuforums.net/showthread.php?61623-How-I-got-this-fixed-gt-KDE-cannot-logout-shutdown-reboot-etc](https://www.kubuntuforums.net/showthread.php?61623-How-I-got-this-fixed-gt-KDE-cannot-logout-shutdown-reboot-etc) 
  According to this thread, this config file correlates to several "strange" bugs in KDE.    
Hope this helps.

---

### Post by thomass4 on 2015-12-14
I had a similiar problem as timgood: 
- I got the same "This operation cannot continue since proper authorization was not provided" error
- I could not start any terminal or Dolphin instance, nor did the Application Launcher Button work 
- My startup scripts were not executed (autostart)
- However, switching to a terminal using strg+alt+F2 did work properly and I was able to run apt-get update+upgrade

For completeness (maybe it would help someone), here how I solved the problem:
I realized that kate (my default text editor) was loading after login but unfortunately never was able to start (I still do not know why). So I killed kate by switching to terminal using strg+alt+F2 and 'pkill kate' after logging in. Then suddenly everything worked and all startup scripts were executed properly again. I had a look at ~/.kde/Autostart/ and found a file hs_err_pid2268.log in there which was probably produced by the Java Runtime Environment (as it was stated in the header). After removing this file, kde started without any problems during the next login :)

---

