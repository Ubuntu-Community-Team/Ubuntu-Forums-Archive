---
title: "Screen lock and blank screen does not work in 20.04 LTS"
date: 2023-03-08
forum: General Help
---

### Post by Shobuz99 on 2023-03-08
Hi.
I recently upgraded my HP Elitebook 8460P laptop from 18.04 LTS to 20.04 LTS.
I had backed up the files from the 18.04 version.
I installed the 20.04 version with a CD and all went well.
I went to the Settings section, selected Privacy and then selected Screen Lock.
I kept the Blank Screen Delay to **1 minute**.
I selected Automatic Screen Lock to **on**.
I selected Automatic Screen Lock Delay to Screen Turns **off**.
I left Lock Screen On Suspend to **Off**.
I left Show Notifications On Lock Screen to **off**
I exited Settings.

Prior to restoring my backed up files to the new 20.04, the screen lock worked as expected.
Once I restored my files, the screen lock & blank screen stopped working.
The screen sits there without any change.
I can manually lock the screen without issue and after a minute it goes into Suspend.
Then I press the Power button, and it asked for my password

I've searched for this problem in previous posts here, but have not found my situation.

Today I changed my resolution to 1360 x 768 (16:9) from 1366 x 768 (16.9) which was the default (?),
because my log file showed an error that *1366 is not divisible by 4*
So far after power off and then start from old boot, that change has not affected my issue.

Please let me know what additional information you need from me, help me fix this.

Thank you very much for your response.

**Shobuz99**
**Ubuntu user since version 6.10 in 2006**

---

### Post by DuckHook on 2023-03-08
The key here is: how did you backup and restore? Details please.

I suspect that you overwrote the settings that you selected with an old configuration file when you restored. Without knowing the details, this is just an educated guess.

Ubuntu keeps most of your personal settings in /home/your&#8209;user&#8209;name/.config and /home/your&#8209;user&#8209;name/.local
Apps will also create their own config directories under /home/your&#8209;user&#8209;name/ (example: /home/your&#8209;user&#8209;name/.mozilla)

If you just restore *everything* from your 18.04 /home directory, then your old config files will clobber your new ones. Since there are often subtle changes in config files from one version to the next, old config files may still work but work strangely. These are notoriously difficult to diagnose.

When I restore /home after a version upgrade, I do so selectively. The important stuff is my hard data—photos, docs, music, etc. Anything beyond that, I live with the new defaults. If I do make changes, it is done on the new virgin config files, not by importing the old ones.

This is only true of brand new virgin installs. When I network upgrade, I trust the devs and the larger community to have properly figured out any conflicts beforehand. So far, so good, but your mileage will vary.

---

### Post by Shobuz99 on 2023-03-08
> **DuckHook said:**
> The key here is: how did you backup and restore? Details please.

I suspect that you overwrote the settings that you selected with an old configuration file when you restored. Without knowing the details, this is just an educated guess.

Ubuntu keeps most of your personal settings in /home/your&#8209;user&#8209;name/.config and /home/your&#8209;user&#8209;name/.local
Apps will also create their own config directories under /home/your&#8209;user&#8209;name/ (example: /home/your&#8209;user&#8209;name/.mozilla)

If you just restore *everything* from your 18.04 /home directory, then your old config files will clobber your new ones. Since there are often subtle changes in config files from one version to the next, old config files may still work but work strangely. These are notoriously difficult to diagnose.

When I restore /home after a version upgrade, I do so selectively. The important stuff is my hard data—photos, docs, music, etc. Anything beyond that, I live with the new defaults. If I do make changes, it is done on the new virgin config files, not by importing the old ones.

This is only true of brand new virgin installs. When I network upgrade, I trust the devs and the larger community to have properly figured out any conflicts beforehand. So far, so good, but your mileage will vary.

Thank you for the reply. You guessed correctly.

I used the Backup (deja dup) on 18.04.5 and the Restore option on 20.04.5.
What other details would help?
I'm guessing there may be a difference between the 18.04 & 20.04 versions of Backup (deja dup)? Would that affect anything?
Re: restoring selectively - I didn't do that unfortunately. Creature of habit. :redface: :-(
I don't remember using "selective restore" but I'm assuming I can run restore from the 20.04 CD and then select the files to restore from the list? Or is it not that simple?

I looked in my .config folder and there are 8 files and 35 folders within the .**config** folder
Out of the 8 files,

mimeapps.list (no effect)
monitors-v1-backup.xml 
monitors.xml are recently modified because I changed the resolution today from 1366x768 to 1360x768 because an error msg in a log file said "1366 is not divisible by 4".
I thought that might've had an effect.

user-dirs.dirs                     modified 10 Mar 2022
lxtask.conf                         modified 7 Oct 2020
Trolltech.conf                    modified 24 Nov 2018
gnome-initial-setup-done  modified 25 Oct 2018
user-dirs.locale                 modified 27 Oct 2017

I haven't begun to view the 35 folders contents.

12 folders were modified 2017
  3 folders were modified 2018
  1 folder was modified 2019
  2 folders were modified 2020
  1 folder was modified 2021
  4 folder were  modified 2022

And the rest were modified when I installed 20.04

I can see *now* that I've caused myself some work, depending on how many of these folders/files need to be replaced or deleted.

As you can see, I waited a bit too long to upgrade from 18.04 to 20.04, in my own opinion.
I'm 73 now and if I don't do things regularly on my computer that involve system features, etc., I forget what I did. :-(
I DO bookmark Ubuntu Forums files that I've gotten help from many different moderators, including you of course!
But I couldn't find any of those anywhere in my files or bookmarks.
Incidentally, I went from 14.04 right through to 18.04. I tried 16.04 and hated it..
Sorry, I guess that's a bit harsh, but it wasn't friendly to me. ;-)

If you need more information, just say so. I'll post whatever you need.
Thanks again for your help.
I appreciate it DuckHook! :D

Shobuz99..

---

### Post by DuckHook on 2023-03-08
This is not really that much of a problem, so let's not get discouraged.

When I back up for a new install, I don't use Deja Dup. I just copy the contents of Documents, Downloads, Pictures, Videos, Music and Templates to an external disk, then check to see that it's all accessible. I also include the directories .mozilla, .thunderbird and .config/BraveSoftware (if you use Brave Browser which comes highly recommended by me). This is usually where most people have all of their hard data. Once these directories are safeguarded, the rest are all optional.

Despite the fact that the following are "optional", I find that having them is still nice so they get backed up too:

Directories
~/.local/share/applications/ (for custom .desktop files you may have created)
~/.local/share/rhythmbox/ (for playlists)
~/.local/share/backgrounds/ (for favourite desktop backgrounds)
~/.local/share/gnucash/ (but only if you use gnucash)
~/.config/gnucash/ 
~/.config/autostart/ (for applets that you autostart on boot)

Files
~/.bashrc
~/.bash_history
~/.bash_aliases
~/.screenrc

This isn't an exhaustive list and you can include more if you want. But be careful not to include too much. Everything else not only *can* be set up again after install but one might even argue that they *ought* to be set up again. Doing so is what will give you those clean config files that you want.

I don't know how far along you are in customizing your new install, but if just at the early stages, you may wish to consider installing again&#8212;this time, not using Deja Dup but doing a simple copy &#8594; paste of the above directories/files. Copy the selective data over to your new install before customizing it.

---

### Post by DuckHook on 2023-03-08
I should note that you should backup ***everything***. That's the safe thing to do. It's just that you then restore only ***some*** things.

I'm sure you get my drift.

---

### Post by Shobuz99 on 2023-03-08
> **DuckHook said:**
> This is not really that much of a problem, so let's not get discouraged.

When I back up for a new install, I don't use Deja Dup. I just copy the contents of Documents, Downloads, Pictures, Videos, Music and Templates to an external disk, then check to see that it's all accessible. I also include the directories .mozilla, .thunderbird and .config/BraveSoftware (if you use Brave Browser which comes highly recommended by me). This is usually where most people have all of their hard data. Once these directories are safeguarded, the rest are all optional.

Despite the fact that the following are "optional", I find that having them is still nice so they get backed up too:

Directories
~/.local/share/applications/ (for custom .desktop files you may have created)
~/.local/share/rhythmbox/ (for playlists)
~/.local/share/backgrounds/ (for favourite desktop backgrounds)
~/.local/share/gnucash/ (but only if you use gnucash)
~/.config/gnucash/ 
~/.config/autostart/ (for applets that you autostart on boot)

Files
~/.bashrc
~/.bash_history
~/.bash_aliases
~/.screenrc

This isn't an exhaustive list and you can include more if you want. But be careful not to include too much. Everything else not only *can* be set up again after install but one might even argue that they *ought* to be set up again. Doing so is what will give you those clean config files that you want.

I don't know how far along you are in customizing your new install, but if just at the early stages, you may wish to consider installing again—this time, not using Deja Dup but doing a simple copy &#8594; paste of the above directories/files. Copy the selective data over to your new install before customizing it.

I am considering installing again, however the only backup I have is in deja dup format, ie compressed.
So unless I can restore selectively from deja dup, I have no way of knowing which files to select...or am I misunderstanding what you said??

---

### Post by DuckHook on 2023-03-08
You can do another backup right now, uncompressed and not using deja dup. Just drag the whole of your /home directory to an external HDD and you are done.

Make sure that you can read everything on the external disk though.

There is a way to restore selectively from deja dup, but I would not bother, given how simple it is to just do the above. Keep your deja dup backup as an additional insurance.

---

### Post by Shobuz99 on 2023-03-08
Ok. I'll give it a try tomorrow and let you know what happens.
Thank you DuckHook!
:) :D :cool:
Shobuz99

---

### Post by Shobuz99 on 2023-03-12
Hi DuckHook,

I have hesitated to do the manual copy of the /home directory to an external HDD.
Why?
Because I remembered or realized that, during an installation of a dpkg that required *lightdm*, may be the reason the screen lock/blank won't work.
I already have a display manager that was installed with 20.04.5 LTS. It's *gdm3*.

I'm wondering if the install of *lightdm* as a dependency to whatever dpkg I installed *after* the initial 20.04.5 LTS is in conflict with *gdm3*?
If that's true, then all I may to do is uninstall lightdm and whatever dpkg required it, reboot and then the screen lock/blank screen function will return?

BTW.. the only 2 dpkgs I can remember adding are x11vnc and the ssvnc viewer.
I don't think there are any others, but I could be wrong

I guess what I'm saying is, if I try the uninstall of lightdm, x11vnc and ssvnc and it works, then that's fine.
If not, then I will do everything you recommended from the beginning.

I just wanted to let you know my plan before I actually do it.


Thank you again for your help.


shobuz99

---

### Post by DuckHook on 2023-03-12
Make sure you have a good backup anyway. If you are comfortable with your Deja Dup backup (meaning that you've actually restored some files from it so that you have confidence in its integrity) then that should be sufficient. If not, then monkeying around with system files will always be risky.

If you replaced the default display manager, then, yes, this would be enough to give you wonky behaviour. This is yet another instance of my continuing refrain: "leave one's system as close to its default state as possible."

I don't use vnc, so have no idea why they would require you to replace your display manager. Doesn't make sense. Here's my output from querying both of those packages:
```
duckhook@Zeus:~$  apt depends x11vnc ssvnc
x11vnc
  Depends: openssl
  Depends: tk
  Depends: libavahi-client3 (>= 0.6.16)
  Depends: libavahi-common3 (>= 0.6.16)
  Depends: libc6 (>= 2.34)
  Depends: libcrypt1 (>= 1:4.1.0)
  Depends: libssl3 (>= 3.0.0~~alpha1)
  Depends: libvncclient1 (>= 0.9.10)
  Depends: libvncserver1 (>= 0.9.10)
  Depends: libx11-6
  Depends: libxdamage1 (>= 1:1.1)
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxi6 (>= 2:1.2.99.4)
  Depends: libxinerama1
  Depends: libxrandr2
  Depends: libxtst6
  Recommends: x11-utils
  Replaces: <x11vnc-data>
ssvnc
  Depends: libc6 (>= 2.34)
  Depends: libjpeg8 (>= 8c)
  Depends: libssl3 (>= 3.0.0~~alpha1)
  Depends: libx11-6
  Depends: libxaw7
  Depends: libxext6
  Depends: libxmu6
  Depends: libxt6
  Depends: zlib1g (>= 1:1.1.4)
  Depends: tk
  Depends: openssh-client
 |Depends: bind9-host
  Depends: <host>
    bind9-host
  Depends: procps
  Depends: psmisc
  Depends: xterm
  Depends: stunnel4
  Depends: openssl
 |Recommends: default-jre
  Recommends: <java5-runtime>
    default-jre
    openjdk-11-jre
    openjdk-17-jre
    openjdk-18-jre
    openjdk-19-jre
    openjdk-8-jre

```
Neither hauls in lightdm as far as I can see.

You can go ahead and try purging lightdm and replacing it with gdm3 Note, however, that purging Lightdm is doing something to the guts of your system—your GUI at least. Things will likely be fine, but you need to have a way of recovering if it goes south. If you have an install disk, then this should be enough. If not, then make one first.

---

### Post by Shobuz99 on 2023-03-12
Thank you! That's a bit of a relief. 
With your advice and what you showed here re: x11vnc & ssvnc not requiring lightdm, then I'll go back to your original advice and drag my /home directory to a folder on my backup HDD.
Once I'm satisfied with that I'll do a fresh install of 20.04.5 LTS.
If that all looks good and works as expected, including the screen lock & blank screen, then I'll *gingerly, selectively & cautiously restore* from the home directory folder on my backup HDD.
If anything else occurs that's wonky, I'll try to work through it before I continue this thread.
I promise I'll mark this solved as soon as I solve it.

UPDATE: Everything worked out the way you said it would, by following your advice.
I appreciate your help.
BTW..I think I will upgrade again to 22.04 in 2 about months because I want to hang on to it for 5 years.
If I do, I'll be 78 yrs old by then LOL! And I'll still be an Ubuntu user TTDID!
:):D=d>8-)
Thank you again for your help!

shobuz99

---

