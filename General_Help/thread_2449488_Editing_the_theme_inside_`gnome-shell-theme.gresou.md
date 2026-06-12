---
title: "Editing the theme inside `gnome-shell-theme.gresource` prevented Ubuntu from starting"
date: 2020-08-27
forum: General Help
---

### Post by solebay-sharp on 2020-08-27
I was naively editing gnome-shell-theme.gresource while trying to edit the login/lock-screen background. The full path is given below:

```
/usr/share/gnome-shell/theme/Yaru/gnome-shell-theme.gresource
```

More specifically I changed what was under the #lockDialogGroup section. This prevented my laptop from booting.


If you run UBUNTU and have a moment: Could you please let me know what is under your #lockDialogGroup in both: /usr/share/gnome-shell/theme/Yaru/gnome-shell-theme.gresource  and /usr/share/gnome-shell/theme/gnome-shell-classic.css (I  made a change here to at one point but thought I successfully edited it  back after it had no effect). This might save my bacon.


When failing to boot the following would appear (basic terminal-like white text against black background, I can't recall the precise numbers):

```
/dev/sda2: clean 12345678/12345678 files 12345678/12345678 blocks
```

Then, a [graphically superior message comes up]("https://user-images.githubusercontent.com/7460774/65824196-14f6e100-e222-11e9-8537-93c27d695adb.jpg") (grey text against a white background):

[INDENT]:( Oh no! Something has gone wrong! A problem has occurred and the system can&#8217;t recover. Please contact a system administrator


[/INDENT]
Using ctrl + alt + F3 I was able to login without a GUI, and undo the  changes based on the contents of the same file. This was possible as I  could boot another laptop from USB and select "Try Ubuntu", then just sudo nano path/to/gnome-shell-theme.gresource.

This did not get me past the error...


[HR][/HR]Some basic troubleshooting:

I ran a bad blocks test to be safe, but it found no HDD failures.

I booted in recovery mode and selected fsck but this occurs:

```
/lib/recovery-mode/recover-menu: line 80: /etc/default/rcS: No such file or directory
fsck from util-linux 2.34
/dev/sda2 is mounted
e2fsck: Cannot continue, aborting.
```

I also reinstalled GRUB from the Ubuntu on my USB just in case. This didn't seem to do anything.

When I accidentally held F4 on boot in addition to the the /dev/sda2 message I am given two messages saying there is a problem loading x.509 certificates -65.

[HR][/HR]
Any ideas and indeed criticisms welcome. I would be particularly keen to know if I can reinstall EVERYTHING inside my /usr/share/gnome-shell/theme  file. Can one reinstall the default OS theme from terminal? Thank you  for reading the above, I did try to balance detail with brevity.

---

### Post by deadflowr on 2020-08-27
You need to extract the css file from the gresource database file.
Then edit the css file and rebuild the gresource file.
Never edit the gresource file directly.
Some help on how-to (hopefully) found here: [https://askubuntu.com/questions/1227070/how-do-i-change-login-screen-theme-or-background-in-ubuntu-20-04]("https://askubuntu.com/questions/1227070/how-do-i-change-login-screen-theme-or-background-in-ubuntu-20-04")

From my own experiences playing with this, make a backup copy somewhere first, before doing any editing or extracting.
(Best to save it somewhere you have quick access to like your home /Documents folder.
That way if you mess up (again) you can just copy back the riginal and try again later)


That said, a quick fix to load a login screen would be to install lightdm and set it as the display manager.
This will at least allow you to load the desktop.
Should be able to switch to a tty session (ctl+alt+F2-8] and login there and run
```
sudo apt install lightdm
```
type reboot to reboot and you should get the lightdm login screen, which should allow you to login.

---

### Post by solebay-sharp on 2020-08-27
I installed lightd but for some reason after succesfully logging in (further progress than before) , I get the same crash error as before. Additionally, when I run the command

```
 update-alternatives --config gdm3-theme.gresource
```

unlike in the guide I am told there is only one gdm3 choice? I don't know if this constitues an issue.

Furthermore, running
```
gresource extract /usr/share/gnome-shell/theme/Yaru/gnome-shell-theme.gresource /org/gnome/shell/theme/gdm3.css > $HOME/gdm3.css
```

[FONT=arial]provides only a blank file when I try to open it with nano? Is this because nano wont open a css file? Do I desperately need a GUI?[/FONT]

---

### Post by cg-152 on 2020-08-27
Do you have the libglib2.0-dev package installed? It's needed to properly extract and pack .gresource files.

I had an issue similar to this [earlier]("https://ubuntuforums.org/showthread.php?t=2448670"), and I think the simplest way to fix the .gresource file is to grab the entire file from somewhere else like a live cd or by downloading the .deb of yaru-theme-gnome-shell (and manually extracting) replacing your .gresource file, then reboot.

---

### Post by solebay-sharp on 2020-08-27
You are correct but I don't know how best to aquire a functional copy of Yaru. Forgive my ignorance but I thought a copy might be available from GitHub. I only own one device so a total install of Ubuntu from which to copy is not feasible.

And yes, libglib is definitely installed.

---

### Post by solebay-sharp on 2020-08-27
Good lord your suggestion worked. Why did I not try this sooner??

```
 sudo apt-get update
```

```
 sudo apt purge yaru-theme-gnome-shell
```

Then after seeing a related warning about Yaru NOT being deleted... (You *will* die you mutated abomination)

```
cd /usr/share/gnome-shell/theme/Yaru

sudo rm -r Yaru 
```

Now for a fresh install...
```
sudo apt-get install yaru-theme-gnome-shell
```

Restart using...
```
service gdm restart 


```


Done!

---

### Post by solebay-sharp on 2020-08-27
Oh God no, it didn't work, I am now stuck in a loop. Every time I login I go back to the login page!

---

### Post by cg-152 on 2020-08-27
First, try reinstalling gdm as well (sorry if it wasn't clear, but I meant downloading the .deb and only extracting the .gresource file). Also, try temporarily disabling your extensions in ~/.local/share/gnome-shell/.

---

### Post by solebay-sharp on 2020-08-28
Thank you for your patience and sticking with me while I muddled through @cg-152. It's really good to know other people have set their minds to offering help when things aren't going well. I managed to fix the issue in the end.

For anyone else who edits important files without backups....

I found a way to undo this mess. 

Use **ctrl** + **alt** + **F3** to access tty, basically interface with the computer without any GUI.

Purge the mutilated version of gdm3 that is punishing its creator who made edits without a backup.

```
     Sudo apt purge gdm3
```

Go and delete your Yaru folder manually if it still exists. I got a message saying mine did.

    ```
cd /usr/share/gnome-shell/theme/

    ls
```

Yup, damn thing was still there, clinging on for dear life.

```
     sudo rm -r Yaru
```

Install fresh gdm3

```
     sudo apt install gdm3
```

```
     sudo apt install-desktop-theme-minimal
```

Start user interface by running...

```
     startx
```

Reconfigure gdm3

```
     sudo dpkg-reconfigure gdm3
```

The above only seemed to get me from a boot-loop to a login-loop so I also had to change some permissions...

```
     sudo chmod a+wt /tmp
```

Hopefully, you can now successfully login. And if you want to edit your login screen you can use [this script from thiggy01][1] instead of bricking your OS.


  [1]: [https://github.com/thiggy01/ubuntu-20.04-change-gdm-background](https://github.com/thiggy01/ubuntu-20.04-change-gdm-background)

---

### Post by cg-152 on 2020-08-28
Thanks for sharing the solution you found, good luck in changing your background!

---

### Post by tea for one on 2020-08-28
> **solebay-sharp said:**
>  And if you want to edit your login screen you can use [this script from thiggy01][1] instead of bricking your OS.

  [1]: [https://github.com/thiggy01/ubuntu-20.04-change-gdm-background](https://github.com/thiggy01/ubuntu-20.04-change-gdm-background)

Thanks for the link - it's a good find

---

### Post by blazking on 2020-12-15
> More specifically I changed what was under the #lockDialogGroup section. This prevented my laptop from booting.

Same here. 
I installed ubuntu alongside win10 on a new laptop (asus g14), and as I wanted to change the login page I ended up editing the ***gnome-shell-theme.gresource*** file -in the Yaru theme folder- as I could not see any .css ones as in previous versions.
I then had a black screen when I wanted to log in (didnt "see" any error messages). 
I re-edited the concerned file later on, putting the only value I changed back to its default one (under #lockDialogGroup). I paid attention to spaces and all...but I kept having a black screen on login.
From what I've read on this thread and others, 'seems like a bad idea to play w/ this file :). 

For other folks who would read this post later on, here's what I did to solve the issue in my case : 

**1. **chose "Advanced options for Ubuntu" -> why ? Because you'll want to use the command line to fix the error. 
**2. **make sure you "Enable networking" (I had a rj45 cable plugged into a usb-c adapter, glad this one worked smoothly :D). 
**3.** chose "Drop to root shell prompt" -> why ? to load a shell prompt as root 
**4. **As explained above, editing the file back to its original version did not seem to work (didnt look "why" yet, but I'd be curious to understand as I'm pretty sure I had correctly edited the file back to its original version).
So from here I did the following : 
***a)*** switched back to my user from root (su your_user), as I was not sure if there was any "context awareness" regarding this theme "thing". 
***b) ***Then, I simply re-installed the Yaru theme package (similarly as proposed in OP post here : [https://ubuntuforums.org/showthread.php?t=2449488&p=13982398#post13982398](https://ubuntuforums.org/showthread.php?t=2449488&p=13982398#post13982398) ) but with the following : [B]sudo apt-get install --reinstall gnome-shell-extensions yaru-theme-gnome-shell
[/B]
I'm now back to my "purple-ish" login.

---

