---
title: "Nautilus Shows Hidden Folders By Default"
date: 2013-04-07
forum: General Help
---

### Post by Rikeshar on 2013-04-07
Using Ubuntu 13.04. Like the title says, when I open Nautilus it automatically shows all the hidden folders. Any ways to get back to not showing them by default?

---

### Post by Frogs Hair on 2013-04-07
Try Ctrl + h , hidden folder view is persistent on Nautilus 3.6.3 like Thunar.

Edit: Make sure show hidden is not enabled in preferences either.

---

### Post by Rikeshar on 2013-04-07
No, it's not here for some reason. If I press ctrl+h to hide the folders, close the windows and reopen it, they're all showing again.

nautilus --version shows I'm using Nautilus 3.8.0

---

### Post by breezypt on 2013-04-07
Did you do a sudo apt-get update, then try to remove and reinstall Nautilus? If you have trouble with the command line use the 'Synaptic Package Manager' and mark nautilus for 'complete removal' then reboot, then do a reinstall. If you don't have the synaptic package manager you can get it form the software manager. In Synaptic when you mark something it gives you a choice of whether to remove, completely remove, or install. It also fixes broken packages. You can try to type in Nautilus in the search box then click on broken on the left side of the pane, it may fix it in Synaptic.

---

### Post by steeldriver on 2013-04-07
what does 

```
dconf dump /org/gnome/nautilus/preferences/
```

say?

---

### Post by Frogs Hair on 2013-04-07
> **Rikeshar said:**
> No, it's not here for some reason. If I press ctrl+h to hide the folders, close the windows and reopen it, they're all showing again.

nautilus --version shows I'm using Nautilus 3.8.0

 I am running 13.04 and didn't upgrade to gnome 3.8 so I have 3.6 .

---

### Post by stinkeye on 2013-04-08
Using the terminal, get your current dconf setting...
```
gsettings **get** org.gnome.nautilus.preferences show-hidden-files
```

Reset to default (false)...
```
gsettings **reset** org.gnome.nautilus.preferences show-hidden-files
```


Check again (should show false)...
```
gsettings **get** org.gnome.nautilus.preferences show-hidden-files
```
Should now always revert to not showing hidden files once nautilus is closed.

---

### Post by Rikeshar on 2013-04-08
Well,
```
gsettings get org.gnome.nautilus.preferences show-hidden-files
```

Does return false, yet it is still showing them by default.

This:
```
[COLOR=#000000][FONT=Ubuntu Mono]dconf dump /org/gnome/nautilus/preferences/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

returns:
[/FONT][/COLOR]```
default-folder-viewer='icon-view'[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]always-use-browser=true
click-policy='double'
show-advanced-permissions=false
enable-delete=false
```

---

### Post by malabarth on 2013-04-23
I have the same problem too!
Even if I uncheck the option, Hidden files are display again on the next nautilus window I open! :/

```
$ dconf dump /org/gnome/nautilus/preferences/
    show-hidden-files=false
    always-use-location-entry=true
    sort-directories-first=true

$ [COLOR=#000000][FONT=Ubuntu Mono]gsettings get org.gnome.nautilus.preferences show-hidden-files[/FONT][/COLOR]
    False
```

EDIT: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1171852](https://bugs.launchpad.net/ubuntu-gnome/+bug/1171852)

---

### Post by sonux on 2013-04-28
open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

---

### Post by MARP1961 on 2013-05-10
> **sonux said:**
> open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

That's solved this irritating bug. Many thanks!

---

### Post by -jay- on 2013-06-30
thank you sonux

that worked for me also

---

### Post by spider623 on 2013-09-28
> **sonux said:**
> open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

Thanks @sonux that one actually helped, i'm on 13.10 btw

---

### Post by Paper Bag on 2013-10-18
That solution worked.

Bug appeared to me after upgrading to 13.10. All other things it seemed remember (the two things the new-Nautilus still remembers in the first place; sort by, reversed order). Somehow the bug reapperead even after applying that solution. Not sure why: only related thing I did was editing manually gtk3 bookmarks (because for some nice reason default bookmarks had been added to the file).

Problem solved for now, but I think this was the last straw for me and I think I've finally had it with this butchered, all the time more useless Nautilus. Soon easier to list things it can do than to list things it can not do.

---

### Post by stinkeye on 2013-10-18
> **Paper Bag said:**
> That solution worked.

Bug appeared to me after upgrading to 13.10. All other things it seemed remember (the two things the new-Nautilus still remembers in the first place; sort by, reversed order). Somehow the bug reapperead even after applying that solution. Not sure why: only related thing I did was editing manually gtk3 bookmarks (because for some nice reason default bookmarks had been added to the file).

Problem solved for now, but I think this was the last straw for me and I think I've finally had it with this butchered, all the time more useless Nautilus. Soon easier to list things it can do than to list things it can not do.
Install nemo. Works well here.
Compact view and more.

---

### Post by Paper Bag on 2013-10-18
> **stinkeye said:**
> Install nemo. Works well here.
Compact view and more.
Goodbye Nautilus. Not really sure why I didn't do this previously, masochism? Can't believe how much I missed some of the old features. <3

---

### Post by Paper Bag on 2013-10-21
This problem just seems to come back randomly. Perhaps something to do with Unity restart (with command 'unity', why I had to do that is unrelated to this problem).

Command (alias) for easier fixing:
```
gsettings set org.gtk.Settings.FileChooser show-hidden false
```

The bug needs more attention so remember to 'star' it if not already done it:

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1171852](https://bugs.launchpad.net/ubuntu-gnome/+bug/1171852)

ps. I couldn't change to Nemo after all (official repos do not have nemo-dropbox, while the Cinnamon repo does have it, it installs Cinnamon 2.0 which kills Unity in 13.10... #-o).

---

### Post by valiopsr on 2014-02-16
> **sonux said:**
> open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

Thank you very much ! That was what actually resolved my problem.

---

### Post by DukeBoxer on 2014-03-14
Guys this happens to me also but I'm not so sure it's a bug as much as a setting that got copied over from the installer. I'm pretty sure that when I installed from a live environment I had "un-hidden" my files so I could get my conky config files copied over to external storage and with nautilus still showing the hidden files I ran the installer. Now when I open a folder the hidden files are being shown. Kind of like when you connect to WiFi in the live CD and then install you automatically connect on the fresh install. Can anyone else confirm this is the reason?

---

### Post by Kevin_Kazienko on 2014-04-26
> [COLOR=#000000]*open terminal and type:*[/COLOR]
[COLOR=#000000]*dconf-editor*[/COLOR]
[COLOR=#000000]*Enter and then:*[/COLOR]
[COLOR=#000000]*org->gtk->settings->file-chooser*[/COLOR]
[COLOR=#000000]*uncheck show-hidden*[/COLOR]

[COLOR=#000000]*Have a nice day!*[/COLOR]
Your response made my day fantastic! Truly a gentleman and a scholar! Thank you :D

---

### Post by saphir89 on 2014-05-22
Hello,
I had the same problem, after adding an icon set into the hidden folder .icons with the Archivemanager.
To solve it, I had to open a .zip file with the Archivemanager again, choose "extract to" and uncheck "show hidden files" with a rightclick again.
After closing everything was fine again.

---

### Post by pancakesurprize on 2014-07-03
> **sonux said:**
> open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

THANK YOU. This is a wonderful solution. :p

---

### Post by pratik patodi on 2014-09-05
Worked for me. Thanks

---

### Post by chrisbakr on 2015-04-13
Hey just wanted to saw thanks for this! there is no way to say kudos or anything, upvote etc. but saved me a lot of time.

---

### Post by lastopier on 2015-05-16
Thanks! I  had the opposite problem and this solved it perfectly!

---

### Post by sago-king on 2015-11-16
> **sonux said:**
> open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

Have a nice day!

Super! thx a lot :)

---

### Post by benjamin-j-wagner-1 on 2015-12-22
> [COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **sonux** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12623240#post12623240")[/COLOR]
[COLOR=#000000][I]open terminal and type:
dconf-editor
Enter and then:
org->gtk->settings->file-chooser
uncheck show-hidden

[/I][/COLOR]
[COLOR=#000000][I]Have a nice day!

[/I][/COLOR]
This worked!  Thank you, **sonux**!

---

### Post by sccjono on 2016-02-22
Whilst the solution posted by sonux works perfectly (and I thank them for this) I can't believe this is still a bug that was reported over three years ago???

jono

---

