---
title: "PCManFM- how do I root?"
date: 2014-07-27
forum: General Help
---

### Post by Robbyx on 2014-07-27
I like to use Pcmanfm both as root and non root, and although I have followed this advice I am not getting any rooted version to run in Docky or unity dock.

What do I do after I have created the file in ~/.local/share/file-manager/actions  ?


> Run as root

You can use Desktop file specification extension (DES-EMA) to add support for opening some folder as root. Example of the desktop entry that implements such feature in file and folder context menus:

[Desktop Entry]
Name = Open as Root
Tooltip = Open the folder as root
Icon = terminal
Profiles = on_folder;

[X-Action-Profile on_folder]
Name = Open as Root
MimeTypes = inode/directory;
SelectionCount = 1
Exec = gksudo pcmanfm %s

You can replace gksudo above with another application that gives you root privileges in dependence which one do you have in your system, such as gksu (Debian Sqeeze) or beesu (Fedora Core).

You can replace pcmanfm above too, with pcmanfm-qt for example.

That file should be put into the directory ~/.local/share/file-manager/actions to take effect.

PCManFM versions 0.4 thru 1.1 had the option in main menu: "Tools" > "Open Current Folder as Root", but now it is removed due to security considerations. 
[http://wiki.lxde.org/en/PCManFM#Run_as_root](http://wiki.lxde.org/en/PCManFM#Run_as_root)

---

### Post by ajgreeny on 2014-07-27
You should only need to right click on the folder you want to open as root.
See [http://lubuntublog.blogspot.com/p/actions_24.html](http://lubuntublog.blogspot.com/p/actions_24.html) which I got to from
[http://ubuntuforums.org/showthread.php?t=2209347](http://ubuntuforums.org/showthread.php?t=2209347)

PS:
I think you need to make sure that the script is made executable for this to work.

---

### Post by bapoumba on 2014-07-27
ajgreeny +1. Had to** killall pcmanfm** though before to see the option in the right click menu.

---

### Post by Robbyx on 2014-07-27
I have followed the instructions, but I can not get it to show as an entry when I right click on a directory. I am using 14.04. Is that the reason? I have noticed that the action file has an extra tab for desktop entry. The content of that tab seem to be capable of  duplicating some of the entries in the action file, although  I have not filled in the tab's boxes.

---

### Post by bapoumba on 2014-07-27
Have you placed it in the right file ?

---

### Post by Dennis N on 2014-07-27
> **Robbyx said:**
> I have followed the instructions, but I can not get it to show as an entry when I right click on a directory. I am using 14.04. Is that the reason? I have noticed that the action file has an extra tab for desktop entry. The content of that tab seem to be capable of  duplicating some of the entries in the action file, although  I have not filled in the tab's boxes.

> You can use Desktop file specification extension (DES-EMA) to add support for opening some folder as root.
Your .desktop file content shown in post #1 is not correct:

You are missing a line **Type=Action** (in red below)

Here is the file (it works) copied from my system (Lubuntu 14.04):
Other lines differ as well, notably **Exec=**
```
[Desktop Entry]
[COLOR="#FF0000"]Type=Action[/COLOR]
Tooltip=Open Folder As Root
Name=Open Folder As Root
Profiles=profile-zero;
Icon=gtk-dialog-authentication

[X-Action-Profile profile-zero]
MimeTypes=inode/directory;
Exec=/usr/bin/gksu /usr/bin/pcmanfm %u
Name=Default profile

```

---

### Post by mc4man on 2014-07-27
> **Robbyx said:**
> I like to use Pcmanfm both as root and non root, and although I have followed this advice I am not getting any rooted version to **run in Docky or unity dock.**

What do I do after I have created the file in ~/.local/share/file-manager/actions  ?

The instructions you've linked are to create a context menu option similar to nautilus-actions in nautilus. 
(the "Type=Action" line is optional & not needed

If you want a quicklist option to open a root pcmanfm for the unity launcher (dock), then you'll need to edit pcmanfm.desktop & add an action just like any other .desktop that has a quicklist entry(s)

As in screen

Edit:
if I was setting up 1 launcher icon to open pcmanfm as either root or normal then would add 2 actions, ie. - 
> .....clipped
MimeType=inode/directory;
Actions=root;new;

[Desktop Action root]
Name=Open as Root
Exec=gksudo pcmanfm %U
TargetEnvironment=Unity

[Desktop Action new]
Name=Open a New Window
Exec=pcmanfm -n %U
TargetEnvironment=Unity

---

### Post by Robbyx on 2014-07-27
Thank you. I have just followed the advice of PC4Man and this time I can see the option in the unity dock to open as root. I wonder if the Run as Root file in ~/.local/share/file-manager/actions is now surplus as I think I  have put its  essentials in the pcmanfm.desktop

---

### Post by mc4man on 2014-07-27
It's not really 'surplus', just another way/option
From the launcher you're opening the browser as root thru a quicklist entry. The ~/.local/share/file-manager/actions/  .desktop is to open a specific folder as root from your normal, not root,  pcmanfm browser thru the r. click context menu.

---

### Post by Robbyx on 2014-07-27
In my case I could not get the r.click context menu to work. No additional entry appeared! Is it connected with 14.04?

---

### Post by mc4man on 2014-07-27
> **Robbyx said:**
> In my case I could not get the r.click context menu to work. No additional entry appeared! Is it connected with 14.04?

what does this show - 
```
ls  ~/.local/share/file-manager/actions
```

---

### Post by Robbyx on 2014-07-27
pcman_root  root_pcman  root_pcman~

---

### Post by mc4man on 2014-07-27
> **Robbyx said:**
> pcman_root  root_pcman  root_pcman~

well that's not going to work, the file needs to be named something.desktop (something is whatever you want..
Before this gets too confusing a couple of questions
(this whole deal is using the method of nautilus-actions, in this case the suggested file to create will only show in pcmanfm, not in nautilus & without nautilus-actions installed
So - 
Are you still using nautilus?
What is your typical text editor? (gedit?

---

### Post by Robbyx on 2014-07-27
> **mc4man said:**
> well that's not going to work, the file needs to be named something.desktop (something is whatever you want..
Before this gets too confusing a couple of questions
(this whole deal is using the method of nautilus-actions, in this case the suggested file to create will only show in pcmanfm, not in nautilus & without nautilus-actions installed
So - 
Are you still using nautilus?
What is your typical text editor? (gedit?

I very seldom use naulilus. If I can I prefer to use pcmanfm. Apart from this current problem pcm has only one other problem and this is the creation of symbolic links. I haven't worked out how to use pcman to do them.

My sole text editor is gedit.

---

### Post by mc4man on 2014-07-27
Then just stick with basically what was posted before.
Remove those files from ~/.local/share/file-manager/actions

Then in a terminal - (this assumes nautilus-actions is not installed, if it is & nautilus is running then nautilus may crash until the file is populated, no big deal..
```
gedit  ~/.local/share/file-manager/actions/root1.desktop
```

Copy & paste this in, blue is change-able if desired, Name = should be the same in both sections, then save.
```
[Desktop Entry]
Name = [COLOR="#0000FF"]Open as Root[/COLOR]
Tooltip = [COLOR="#0000FF"]Open the folder as root[/COLOR]
Profiles = on_folder;

[X-Action-Profile on_folder]
Name = [COLOR="#0000FF"]Open as Root[/COLOR]
MimeTypes = inode/directory;
SelectionCount = 1
Exec = gksudo pcmanfm %[COLOR="#0000CD"]d[/COLOR]
```

I'm using %d on the Exec = line instead of the prev. quoted %s, other possibles would be %U, %F, %f
( if nautilus is handling the desktop then %s will not work

The option should now show in pcmanfm only, (-  when r. clicking on a folder

---

### Post by Robbyx on 2014-07-27
Thank you. That works wonderfully.

Is there anything that can be done for symbolic links from one directory to another?

---

### Post by mc4man on 2014-07-27
> **Robbyx said:**
> Thank you. That works wonderfully.

Is there anything that can be done for symbolic links from one directory to another?
Not sure what you want but take a look at last 2 posts here (#8, #9

[http://ubuntuforums.org/showthread.php?t=2171454](http://ubuntuforums.org/showthread.php?t=2171454)

---

### Post by Robbyx on 2014-07-30
Thank you. Just the solution.

---

