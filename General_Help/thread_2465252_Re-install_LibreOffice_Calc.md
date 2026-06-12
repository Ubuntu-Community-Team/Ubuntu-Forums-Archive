---
title: "Re-install LibreOffice Calc"
date: 2021-07-27
forum: General Help
---

### Post by michael239 on 2021-07-27
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I hope I’m in the right forum for this problem. It concerns re-installing LibreOffice Calc.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I’m running Ubuntu 20.04.2 LTS and that came with LibreOffice installed.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I ran into problems with it’s spreadsheet Calc. In the end I decided to uninstall and then re-install Calc. That shouldn’t be a problem as the Software app offers the options to this. Only it doesn’t work. Uninstalling Calc works fine, but when I try to re-install it I get :
[/SIZE][/FONT][/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288881&stc=1[/IMG][COLOR=#000000][FONT=Arial][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial][SIZE=3]
I only want to re-install Calc, not re-installing LibeOffice completely as I don’t want having to spend hours configuring all of my preferences.[/SIZE][/FONT][/COLOR]
[/LEFT]
Greetings

---

### Post by The Cog on 2021-07-27
You won't have to reconfigure all your preferences - they are stored in your home directory and uninstalling or reinstalling the program wont delete your personal settings. So you can uninstall and reinstall the whole thing if you like.

---

### Post by mIk3_08 on 2021-07-27
This is very strange, uninstalling the LibreOffice Calc. Why should you do that, anyway this is a free open source application.
I think you can install it back by using the Software App. Try searching it in the Software Apps maybe you can find LibreOffice there.
This is I assumed that the LibreOffice Calc was uninstalled properly in your system and I think you can install it back easily by using the Software App.
But If you uninstalled it improperly I don't think you can install it back easily, you have to remove it completely first so that you won't
be mess up installing it back again. But if you have remove it completely, you can install it back again without any delays. 
So you be careful next time so that will never ruin your O.S again.
Good Luck.

---

### Post by Impavidus on 2021-07-27
The error message indicates it's a temporary error. Refresh the list of available software (i.e., check for updates) and try again.

If the problem was caused by your user config files, removing and reinstalling libreoffice calc won't help. Removing and reinstalling won't reset your settings.

---

### Post by rsteinmetz70112 on 2021-07-27
Open a terminal window (ctrl-alt-t) and try:

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install libreoffice-calc
```

---

### Post by mikewhatever on 2021-07-27
This happens when the mirror sync is in process. Just wait about 10 minutes, then try again:

```
sudo apt update
sudo apt upgrade

```

PS: Don't post pictures of terminal text outputs, just copy pase the text.

---

### Post by michael239 on 2021-07-28
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]There is indeed something wrong with ‘Software’. I just tried to install an app I wanted to test, and I got the same error. Tried another one, same result.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]So I’ll try the update/upgrade procedure.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I will let you know what happens.[/SIZE][/FONT][/COLOR][/LEFT]

---

### Post by michael239 on 2021-07-28
Just ran sudo apt update and got :

Hit:1 [http://ppa.launchpad.net/costales/yaru-colors-folder-color/ubuntu](http://ppa.launchpad.net/costales/yaru-colors-folder-color/ubuntu) focal InRelease
Hit:2 [http://ppa.launchpad.net/gambas-team/gambas3/ubuntu](http://ppa.launchpad.net/gambas-team/gambas3/ubuntu) focal InRelease      
Hit:5 [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu) focal InRelease      
Get:6 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Hit:8 [http://ppa.launchpad.net/micahflee/ppa/ubuntu](http://ppa.launchpad.net/micahflee/ppa/ubuntu) bionic InRelease           
Hit:10 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) focal InRelease               
Get:3 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal InRelease [616 kB]
Get:4 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-updates InRelease [616 kB]
Get:7 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-backports InRelease [616 kB]
Get:9 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-security InRelease [616 kB]
Err:3 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:4 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-updates InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:7 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-backports InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:9 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) focal-security InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done     
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch [http://la-mirrors.evowise.com/ubuntu/dists/focal/InRelease](http://la-mirrors.evowise.com/ubuntu/dists/focal/InRelease)  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-updates InRelease' is no longer signed.
E: Failed to fetch [http://la-mirrors.evowise.com/ubuntu/dists/focal-updates/InRelease](http://la-mirrors.evowise.com/ubuntu/dists/focal-updates/InRelease)  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://la-mirrors.evowise.com/ubuntu/dists/focal-backports/InRelease](http://la-mirrors.evowise.com/ubuntu/dists/focal-backports/InRelease)  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://la-mirrors.evowise.com/ubuntu/dists/focal-security/InRelease](http://la-mirrors.evowise.com/ubuntu/dists/focal-security/InRelease)  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-security InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

I don't understand anything of this, but obviously there is something seriously wrong.

---

### Post by westie457 on 2021-07-28
The mirror site you using is definitely broken.
Open 'Software & Updates', in the first tab where it says Download from click in the box and change the server. Close the window and agree to the prompts.
Open a terminal and run ```
sudo apt update
sudo apt upgrade
```Post the output of the first command if any errors.

---

### Post by michael239 on 2021-07-28
OK westie457. That did the trick.
No more errors and LibreOffice Calc has been re-installed.

Problem Solved

---

### Post by mIk3_08 on 2021-07-28
> **michael239 said:**
> OK westie457. That did the trick.
No more errors and LibreOffice Calc has been re-installed.

Problem Solved Just mark this thread solve.
This will saves people in this community  who try to help others in the Ubuntu Forums from wasting their time  looking at threads that are already solved.
And for more info about on how to mark it as solve just "Click here for (Solve thread)" below.

---

