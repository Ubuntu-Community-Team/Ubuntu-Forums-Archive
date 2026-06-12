---
title: "(2019) Running Xfinity Stream in Ubuntu 18.04"
date: 2019-05-22
forum: General Help
---

### Post by daumas77 on 2019-05-22
[FONT=courier new][B]How to install XFinity streaming on Ubuntu Linux
------------------------------------------------
[/B]
This procedure worked on 2019-05-21

OS: Ubuntu 18.04

Firefox: Firefox 60.7.0esr-32  (32-bit)
[FONT=courier new]   Note: I was unable to get the latest v67 (non-ESR) version to work so I went with ESR
[/FONT]
Adobe Shockwave FlashPlayer: 32.0.0.192


Note this was not tested on any other linux flavor or version but may work anyway.


[B]1. Install wine
[/B][INDENT]a. Install the appropriate Ubuntu repository: (from [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu))[/INDENT]
 
      [/FONT][INDENT=2][FONT=courier new]# Ubuntu 19.04

       sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) disco main'

      # Ubuntu 18.10
      sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main'

      [/FONT][FONT=courier new]# Ubuntu 18.04 or Linux Mint 19.x
      sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main'

      # Ubuntu 16.04 or Linux Mint 18.x
      sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main'
[/FONT][/INDENT]
[INDENT][FONT=courier new] 
[/FONT][/INDENT]
[FONT=courier new] [INDENT]b. Update packages
            [/INDENT]
[INDENT=2]sudo apt update[/INDENT]
[INDENT] 

      c. Install wine
            [/INDENT]
[INDENT=2]sudo apt install --install-recommends winehq-stable 
[/INDENT]
 

[B]2. Download the latest 32-bit offline Firefox ESR and Adobe FlashPlayer installers
[/B]
[INDENT]a. Download 32-bit Firefox offline ESR installer here (select the 32-bit version in your lang)
            [/INDENT]
[INDENT=2][https://www.mozilla.org/en-US/firefox/organizations/all/](https://www.mozilla.org/en-US/firefox/organizations/all/)
[/INDENT]
[INDENT] 


   b. Download Flash Player for Firefox and Netscape Plug-In compatible applications &#8211; NPAPI
            [/INDENT]
[INDENT=2][https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/install_flash_player.exe](https://fpdownload.macromedia.com/pub/labs/flashruntimes/flashplayer/install_flash_player.exe)
[/INDENT]
[INDENT] 

[/INDENT]
 [B]3. Install 32-bit Firefox ESR with a GUI workaround
[/B][INDENT]a. Remove any previous .wine directory to start from scratch
            [/INDENT]
[INDENT=2]rm -rf .wine #assumes you are in your home dir[/INDENT]
[INDENT] 

      b. Allow the initial install of Firefox to automatically create the default .wine dir for you

            [/INDENT]
[INDENT=2]wine "Firefox Setup 60.7.0esr-32.exe"[/INDENT]
[INDENT] 

      c. Follow the prompts, and launch Firefox at the end.
            [/INDENT]
[INDENT=2]Note: The initial launch of FF will create the default FF profile containing prefs.js[/INDENT]
[INDENT] 

      d. Exit Firefox


      e. Install GUI workaround

            [/INDENT]
[INDENT=2](EZ Method)

             1. Run this command

                   [/INDENT]
[INDENT=3]echo 'user_pref("browser.tabs.remote.autostart", false);' >> "`find .wine -name prefs.js`"[/INDENT]
[INDENT=2] 
            (Manual Method)
             1. Locate prefs.js
                   [/INDENT]
[INDENT=3]find .wine -name prefs.js[/INDENT]
[INDENT=2] 
              2. Edit prefs.js with your favorite editor and ADD this line at the end:
                   [/INDENT]
[INDENT=3]user_pref("browser.tabs.remote.autostart", false);
[/INDENT]
[INDENT]
[/INDENT]
 

[B]4. ** IMPORTANT STEP HERE **
[/B][INDENT]Change Windows installation type to Windows XP. By default, the windows installation is set to Windows 7.
      a. Run winecfg


   b. Change "Windows Version" to [Windows XP]


   c. Click OK
[/INDENT]
 


[B]5. Install 32-bit FlashPlayer
[/B][INDENT]a. wine install_flash_player.exe


      b. Check [x] I have read and agree...., Click Install


      c. If you get a 'File not found.' dialog, you must have skipped step 4, in which case go back to 4.


      d. Select (*) Never check for updates, Click DONE
            [/INDENT]
[INDENT=2]Note: the reason for this step is to avoid having an auto-update break your installation
[/INDENT]
 


[B]6. Run FireFox.
[/B][INDENT]a. Double-click the desktop FF launcher (created earlier during the FF install)


      b. Click 'Trust and Launch' if an 'Untrusted application launcher' form appears
[/INDENT]
 

[B]7. Configure FireFox
[/B][INDENT]a. Disable auto-updates (since an update of FF may break this set up)
            [/INDENT]
[INDENT=2]1. Click Options (under the main menu 'burger' icon, upper right of the window)
            2. Scroll all the way to the bottom, then up just a bit to locate 'Firefox Updates'[/INDENT]
[INDENT=2]3. Select/De-select these items:
[/INDENT]
[INDENT=3]Select
[/INDENT]
[INDENT=3](*) Check for updates but let you choose to install them
                  De-select
                  [ ] Use a background service to install updates
                  [ ] Automatically update search engines
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT]  
      b. Enable FlashPlayer Plug-in
            [/INDENT]
[INDENT=2]1. Click Add-ons (under the main menu 'burger' icon, upper right of the window)
            2. Click Plugins
            3. Select [Always Activate] next to 'Shockwave Flash'
[/INDENT]
[INDENT]
[/INDENT]
 

[B]8. Pat yourself on the back, you are done.
[/B][INDENT]a. Navigate to [http://xfinity.com/stream](http://xfinity.com/stream) and log in.
      b. Enjoy!
[/INDENT]
 

[/FONT]

---

### Post by Autodave on 2019-05-22
Thank you for posting this.  I had long ago had it running through WINE, but ended up having to install WIN10 for a particular program and then forgot about using WINE.

I wish that Infinity would just let us use it instead of blocking us.  Doesn't make any sense.

---

