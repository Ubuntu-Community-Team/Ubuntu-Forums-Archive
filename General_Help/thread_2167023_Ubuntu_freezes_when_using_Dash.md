---
title: "Ubuntu freezes when using Dash"
date: 2013-08-12
forum: General Help
---

### Post by bill23 on 2013-08-12
A number of times over the past couple of weeks my PC has frozen up on me and it always happens when I open Dash while I happen to also have one of my browsers open. When this happens the only way out is to power off by way of the Tower then boot back up. I can move my mouse around all I want and left or right click till the Cows come to roost and nothing happens. 
I have heard it was a stability issue with Unity an that I should g for a more stable distro such as: Debian.  I would like to hear from anyone who has had similar troible an what they did to overcome the dilemma?
At the moment I am using a gnome 3.4 desktop environment and so far so good.
bill23

---

### Post by larry3 on 2013-08-12
I am trying to isolate a similar problem. I have found that the problem occurs much more frequently when I am using Chrome as opposed to Firefox. I am using 12.04 LTS, Unity Desktop, Nvidia GeForce 8300 GS drivers. I have as secure shell deamon running so when the desktop freexes, I can still log in from another computer using ssh. So the Linux kernel is still intact. What I see is the Xorg is using 100% of the CPU. I believe the ssh still works because I have a dual core CPU so that the other CPU is still functioning. The fact that Xorg is using 100% CPU suggests the possibility that the problem is in the nVidia driver. Although from you are saying the Unity desktop is also suspect. Perhaps it is the combination. I'm trying to figure out if I have the latest driver. What video card are you using?

---

### Post by bill23 on 2013-08-13
larry3;

I am not all that positive but i think my viedo card is the: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)

I ahve also hard about Unity being suspect. You say you have had the freeze when you were using Chrome? I was adviced to do a update; sudo apt-get update  to see if that may have corrected the issue? I won't know until it happens again, should it ever happen again?

I am even considering installing the Xubuntu desktop. I have heard it is stabler then Ubuntu with Unity?

---

### Post by bill23 on 2013-08-16
bill23
Had another freeze yesterday while using Dash. I was opening the 'Opera Next' browser and right clicked it with the intent of seeing if I could add it on the launch bar. Then bingo it froze up on me. Had to power off through the Tower then reboot. I am using Gnome Fall back option (Gnome 2) to write this. I am still debating whether to ass the Xubuntu desktop or not??
I may try a experiment that of opening Dash and right clicking one of the Apps and see what happens, if anything?

---

### Post by larry3 on 2013-08-18
I updated my nVidia driver and switched to the old Gnome desktop and the problem seems to have cleared up. I guess I will try Unity again to see which of these two things was at fault. But I suspect it may be the interaction of the two. I've searched posts on various forums and the common thread seems to be the combination of nVidia and Unity. Looking at about a half dozen posts where the person gave enough information, I couldn't find anyone complaining of freezes that didn't have this combination. The fact that the xorg process, which is the nVidia x-server, had 100% CPU also supports this hypothesis. I also found something in the release notes of the nvidia update that said it fixed a problem that could cause a crash.

---

### Post by kunaguvarun on 2013-08-20
I'm facing a similar problem. Unity freezes and only a hard reset and no other solution :(

---

### Post by larry3 on 2013-09-02
Although the freezes were less frequent with the classic gnome desktop than Unity, it still happened occasionally. If you have no other way of accessing the system except the desktop, then you have to hard reset. If you have a telnet or secure shell server running, you can log in from another computer. I have switched from the nVidia driver to the nouveau driver and have not had a freeze.

I had problems installing the latest nVidia driver (319) so I don't know if it fixes the problem. I had the freeze problem with versions 304 and 310.

The only downside of nouveau is that Google Earth and other applications that need accelerated graphics don't work very well. Unlike nVidia that requires a complex rigmarole to install, nouveau is part of the main Linux tree.

---

### Post by bill23 on 2013-09-23
To any and all;

I had another freeze a few minutes ago. My first in almost two weeks. I had just clicked on Dash with the intent of checking the Software Updater but did not even get that far as it all froze. I of course went through the useless routine of clicking this that and the other to no avail. Finally to power off my PC I had to use the power button on the Tower then restart. 

I am now using the Gnome 3 desktop environment with which I've not had any problems as with Unity. I don't look for any change with the upcoming Ubuntu 13.10, seeing how this problem is so infrequent as to be naught but a nuisance. What say all of you? 

bill23

---

### Post by mogsareus on 2013-09-25
I don't recollect having this problem until I installed 13.04 a few weeks ago. The system now locks up under a variety of conditions. Dash will sometimes open but if 'more items' are requested the system freezes, the screen changes to a pattern with no way out other than powering off. 
It can crash in a similar manner after entering my password. 
The other day it did it as I pressed the large shutdown button.
When things are running correctly I've tried the suggested  /usr/lib/nux/unity_support_test -p and got the message Error: unable to open display.
I'm not an expert in these things but after considering it a graphics problem decided that it must be something else because everthing else works exactly as it should.
All ideas welcome.

---

### Post by bill23 on 2013-09-26
I had another experience with a freeze whilst using Unity and Dash earlier today. It was only a couple days since the last freeze up. i had this problem when I had Ubuntu 12.04. Presently I am running Ubuntu 13.04 which I installed from a DVD live/install disc. My opinion is it is Unity which is the main contributing factor behind the occurrences of the freeze ups? I can not really blame Dash except the freeze ups usually happen milliseconds after clicking the Dash Icon on the Support bar which is only there because of Unity.

I continue to use Unity because of the convenience of having some of the frequently used item such as web browser  or email amongst others readily available. Then you trade off that ease with the frustration of the occasional freeze up when you happen to open Dash when a simple click.


I am posting this from a Gnome Fall back desktop environment.


bill23

---

### Post by mogsareus on 2013-09-28
I may have made some progress on this one. Today the machine froze everytime I entered my password and tried to log on. Some times the log on screen would stay displayed. Moving the mouse about causes the display to turn into a block pattern. It is possible to get into a terminal in this condition and close the machine down. However the other senario is that a different pattern appears across the whole of the display and the only way out is to hold the power button down. When I tried to log on as a guest everything worked as it should including the dash. I could then change user and access my account.
I don't have enough experience to know where to look inb these cicumstances but perhaps someone could point me in the right direction.

---

### Post by mogsareus on 2013-10-01
Yesterday I couldn't log in as a guest either. In desparation I re installed 13.04 booting from a CD. It made no difference and the machine locked up at log in and guest log in. I updated/upgraded using the command line, but several packages were 'held back'. Today still not being able to get past log in I opened a command line and did update/upgrade again - there were about 291 packages to install. Having done this and rebooted I was able to get into my account direct from the log in screen. I haven't tried anything in Dash yet - will report in due course.

---

### Post by mogsareus on 2013-10-02
Right. I found the solution. Start in recovery mode. Select repair broken packages and follow instructions. System works now - I've just got to try and remeber how to upgrade the graphics drivers and everything should be back to normal.

---

### Post by bill23 on 2013-10-03
Guess what.. . that's right Ubuntu froze/crashed/fell short or what have you Clyde Beatty.
I was using Ubuntu with Untiy and all seemed to be going relatively  smoothly. I had Firefox opened an was on 'Got Linux' One of he followers  of my thread here about my freezes posted a statement about burning an  ISO onto to a usb stick. I believed I had something that would work but i  was not sure of its name, i knew it began with the letters 'B' and 'r'  So keeping Firefox open, I opened Dash and in the search bar had just  typed in those two letters B an r, an that is when it all came tumbling  down a full blow freeze/crash. Following 'Einstein's' definition of  insane' I tried everthing I'd tried before expecting it to work this time but as usually nothing worked.  Except this time the screen went crazy, like what happens when you are watching  an old VHS tape or an old DVD. If that was not bad enough the screen  then went black. 

I had no choice but to power the pc off using the power button on the  Tower and reboot. When the login screen appeared an I saw my choices I  did not hesiate and selected 'Gnome Fallback with no effects' which I am  using now. 

bill23

---

### Post by bill23 on 2013-10-06
Hey to all;

A couple days ago I posted in Launchpad about how my PC was freezing/crashing when I used Dash . I heard back from them and they asked me, what is the output of:

                        [sudo lshw -C display; lsb_release -a; uname -a; dpkg -l | grep gnome-
session-bin]

Here is what I got from that commandline:

[SIZE=4][FONT=palatino linotype]


[/FONT][/SIZE][SIZE=4][FONT=palatino linotype]*-display                [/FONT][/SIZE]
[SIZE=4][FONT=palatino linotype]        description: VGA compatible controller        product: G72 [GeForce 7300 LE]        vendor: NVIDIA Corporation        physical id: 0        bus info: pci@0000:01:00.0        version: a1        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vga_controller bus_master cap_list rom        configuration: driver=nouveau latency=0        resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:efe00000-efe1ffff No LSB modules are available. Distributor ID: Ubuntu Description:    Ubuntu 13.04 Release:        13.04 Codename:       raring Linux bill48-Dimension-9100 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 i686 i686 GNU/Linux ii  firefox-gnome-support                     22.0+build2-0ubuntu0.13.04.2           i386         Safe and easy web browser from Mozilla - GNOME support ii  gnome-accessibility-themes                3.6.5-0ubuntu1                         all          Accessibility themes for the GNOME desktop ii  gnome-applets                             3.5.92-0ubuntu1                        i386         Various applets for the GNOME panel - binary files ii  gnome-applets-data                        3.5.92-0ubuntu1                        all          Various applets for the GNOME panel - data files ii  gnome-backgrounds                         3.8.1-0ubuntu1                         all          Set of backgrounds packaged with the GNOME desktop ii  gnome-bluetooth                           3.6.1-0ubuntu3                         i386         GNOME Bluetooth tools ii  gnome-boxes                               3.6.3-0ubuntu1                         i386         Simple GNOME app to access remote or virtual systems ii  gnome-calculator                          1:3.8.1-0ubuntu1                       i386         GNOME desktop calculator ii  gnome-chess                               1:3.8.1-0ubuntu1                       i386         chess game with 3D graphics ii  gnome-color-manager                       3.6.1-0ubuntu1                         i386         Color management integration for the GNOME desktop environment ii  gnome-contacts                            3.6.2-0ubuntu2.1                       i386         Contacts manager for GNOME ii  gnome-control-center                      1:3.6.3-0ubuntu24.1                    i386         utilities to configure the GNOME desktop ii  gnome-control-center-data                 1:3.6.3-0ubuntu24.1                    all          configuration applets for GNOME - data files ii  gnome-control-center-signon               0.1.6bzr13.04.05-0ubuntu1.1            i386         GNOME Control Center extension for single signon ii  gnome-control-center-unity                1.3daily13.06.19~13.04-0ubuntu1        i386         change the settings of the Unity desktop ii  gnome-core                                1:3.4+7ubuntu4                         i386         GNOME Desktop Environment -- essential components ii  gnome-desktop3-data                       3.6.3-0ubuntu1                         all          Common files for GNOME desktop apps ii  gnome-dictionary                          3.6.0-0ubuntu1                         i386         GNOME dictionary application ii  gnome-disk-utility                        3.6.1-1ubuntu1                         i386         manage and configure disk drives and media ii  gnome-documents                           3.6.2-1ubuntu1                         i386         Document manager for GNOME ii  gnome-exe-thumbnailer                     0.9-0ubuntu2                           all          Wine .exe and other executable thumbnailer for Gnome ii  gnome-font-viewer                         3.7.5-0ubuntu1                         i386         font viewer for GNOME ii  gnome-icon-theme                          3.6.2-0ubuntu1                         all          GNOME Desktop icon theme (small subset) ii  gnome-icon-theme-extras                   3.4.0-2ubuntu1                         all          GNOME Desktop icon theme (additional icons) ii  gnome-icon-theme-full                     3.6.2-0ubuntu1                         all          GNOME Desktop icon theme ii  gnome-icon-theme-symbolic                 3.6.2-0ubuntu1                         all          GNOME desktop icon theme (symbolic icons) ii  gnome-keyring                             3.6.3-0ubuntu2                         i386         GNOME keyring services (daemon and tools) ii  gnome-klotski                             1:3.8.0-0ubuntu1                       i386         Klotski puzzle game for GNOME ii  gnome-mahjongg                            1:3.8.0-0ubuntu1                       i386         classic Eastern tile game for GNOME ii  gnome-media                               3.4.0-1ubuntu1                         i386         GNOME media utilities ii  gnome-menus                               3.6.2-0ubuntu1                         i386         GNOME implementation of the freedesktop menu specification ii  gnome-mines                               1:3.8.0-0ubuntu1                       i386         popular minesweeper puzzle game for GNOME ii  gnome-nettool                             3.2.0-1                                i386         network information tool for GNOME ii  gnome-nibbles                             1:3.8.0-0ubuntu1                       i386         snake game, up to four players ii  gnome-online-accounts                     3.6.2-1ubuntu1                         i386         GNOME Online Accounts ii  gnome-orca                                3.8.0-0ubuntu1                         all          Scriptable screen reader ii  gnome-packagekit                          3.6.0-0ubuntu1                         i386         Graphical distribution neutral software management tools ii  gnome-packagekit-data                     3.6.0-0ubuntu1                         all          Data files for graphical distribution neutral software management tools ii  gnome-panel                               1:3.6.2-0ubuntu3                       i386         launcher and docking facility for GNOME ii  gnome-panel-data                          1:3.6.2-0ubuntu3                       all          common files for the GNOME Panel ii  gnome-power-manager                       3.6.0-1ubuntu1                         i386         power management tool for the GNOME desktop ii  gnome-robots                              1:3.8.0-0ubuntu1                       i386         improved old BSD robots game ii  gnome-screensaver                         3.6.1-0ubuntu3                         i386         GNOME screen saver and locker ii  gnome-screenshot                          3.6.1-0ubuntu2.1                       i386         screenshot application for GNOME ii  gnome-session                             3.6.2-0ubuntu5                         all          GNOME Session Manager - GNOME 3 session ii  gnome-session-bin                         3.6.2-0ubuntu5                         i386         GNOME Session Manager - Minimal runtime ii  gnome-session-canberra                    0.30-0ubuntu2                          i386         GNOME session log in and log out sound events ii  gnome-session-common                      3.6.2-0ubuntu5                         all          GNOME Session Manager - common files ii  gnome-session-fallback                    3.6.2-0ubuntu5                         all          GNOME Session Manager - GNOME fallback session ii  gnome-settings-daemon                     3.6.4-0ubuntu8                         i386         daemon handling the GNOME session settings ii  gnome-shell                               3.6.3.1-0ubuntu6                       i386         graphical shell for the GNOME desktop ii  gnome-shell-common                        3.6.3.1-0ubuntu6                       all          common files for the GNOME graphical shell ii  gnome-shell-extensions                    3.6.0-0ubuntu1                         all          Extensions to extend functionality of GNOME Shell ii  gnome-software-manager                    3.6.0-0ubuntu1                         i386         Graphical distribution neutral software manager ii  gnome-sudoku                              1:3.8.1-0ubuntu2                       all          Sudoku puzzle game for GNOME ii  gnome-sushi                               3.6.1-0ubuntu1                         i386         sushi is a quick previewer for nautilus ii  gnome-system-log                          3.6.1-0ubuntu1                         i386         system log viewer for GNOME ii  gnome-system-monitor                      3.8.0-0ubuntu1                         i386         Process viewer and system resource monitor for GNOME ii  gnome-terminal                            3.6.1-0ubuntu4                         i386         GNOME terminal emulator application ii  gnome-terminal-data                       3.6.1-0ubuntu4                         all          Data files for the GNOME terminal emulator ii  gnome-tetravex                            1:3.8.0-0ubuntu1                       i386         put tiles on a board and match their edges together ii  gnome-themes-standard:i386                3.6.5-0ubuntu1                         i386         Standard GNOME themes ii  gnome-themes-standard-data                3.6.5-0ubuntu1                         all          Data files for GNOME standard themes ii  gnome-tweak-tool                          3.6.1-1                                all          tool to adjust advanced configuration settings for GNOME ii  gnome-update-viewer                       3.6.0-0ubuntu1                         i386         Graphical distribution neutral software update viewer ii  gnome-user-guide                          3.6.2-0ubuntu1                         all          GNOME user's guide ii  gnome-user-share                          3.0.4-0ubuntu1                         i386         User level public file sharing via WebDAV or ObexFTP ii  gnome-video-effects                       0.4.0-1ubuntu2                         all          GNOME Video Effects ii  language-pack-gnome-en                    1:13.04+20130418                       all          GNOME translation updates for language English ii  language-pack-gnome-en-base               1:13.04+20130418                       all          GNOME translations for language English ii  libgnome-bluetooth11                      3.6.1-0ubuntu3                         i386         GNOME Bluetooth tools - support library ii  libgnome-control-center1                  1:3.6.3-0ubuntu24.1                    i386         utilities to configure the GNOME desktop ii  libgnome-desktop-3-4                      3.6.3-0ubuntu1                         i386         Utility library for loading .desktop files - runtime files ii  libgnome-keyring-common                   3.6.0-1                                all          GNOME keyring services library - data files ii  libgnome-keyring0:i386                    3.6.0-1                                i386         GNOME keyring services library ii  libgnome-media-profiles-3.0-0             3.0.0-1ubuntu1                         i386         GNOME Media Profiles library ii  libgnome-menu-3-0                         3.6.2-0ubuntu1                         i386         GNOME implementation of the freedesktop menu specification ii  libp11-kit-gnome-keyring:i386             3.6.3-0ubuntu2                         i386         GNOME keyring module for the PKCS#11 module loading library ii  libpam-gnome-keyring:i386                 3.6.3-0ubuntu2                         i386         PAM module to unlock the GNOME keyring upon login ii  thunderbird-gnome-support                 1:24.0+build1-0ubuntu0.13.04.1         i386         Email, RSS and newsgroup client - GNOME support[/FONT][/SIZE]


From this they determned I was using an open source driver and they suggested I use a Nvidia one instead and so I installed the one with the most updates. I am back with Unity an it is now a matter of waiting to see if he change of drivers made any difference. If a couple weeks goes by and no crashes and or freeze ups happens then I might conclude this 'sucker' is a done dude.

bill23

---

### Post by mogsareus on 2013-10-10
Well I thought I had this resolved but reinstalling the Nvidia drivers didn't work for long. Machine began to crashi at log in. Start in recovery mode, and use it with default graphics whilst I researched the problem further. But if I turned it off it reinstalled the Nvidia drivers and crashed at log in.  Read of Torvalds speech in which he expressed his views about Nvidia. Bought AMD radeon HD5450 graphics card - installed same and now everything is working properly.

---

