---
title: "Right click to destination"
date: 2017-06-10
forum: General Help
---

### Post by Strasmus on 2017-06-10
Hey,

I'm looking for a way to use the right-click menu to copy/move files to a specific location.
As in, right-click on a file and have the option to move it to a specific folder. (ex. to my /home/username/photos

Is that possible?

I tried using the search option, but didn't really anything. Sorry if a solution has already been posted.

---

### Post by ajgreeny on 2017-06-10
This can be very easily done using thunar, the xfce, Xubuntu file manager using its custom actions.

I use many of them including one for "copy to", and another for "move to" but I am not sure if you can do the same using nautilus. the Ubuntu file manager.
I presume it is possible in Ubuntu to install thunar and use that as the default file manager.  I also assume you will need to retain nautilus, as in the past, using gnome desktop, it was nautilus that wrote and managed the desktop; that may have now changed in unity and gnome-3, but as I don't use Ubuntu I can not answer that for you.

If you want to persue this further and install thunar I can let yolu know the details of the move/copy custom action scripts I use for you to try.

---

### Post by Strasmus on 2017-06-10
Thanks for the explanation and suggestion - much appreciated.

Thunar is installed and i ran "exo-preferred-applications" and set thunar as the default file manager.
So where do i go from here, to what i'm looking for?

---

### Post by ajgreeny on 2017-06-11
First install zenity create two shell scripts in your home, **move.sh**, with the following content
```
#!/bin/sh
[ 0 -eq $# ] && exit
dst=$(zenity --title='Where to move' --file-selection --directory) || exit
/bin/mv -n -- "$@" "$dst"
```
the other **copy.sh**, with the following content.
```
#!/bin/sh
[ 0 -eq $# ] && exit
dst=$(zenity --title='Where to move' --file-selection --directory) || exit
/bin/cp -p -n -- "$@" "$dst"
```
and make them both executable.
Now open thunar -Edit -"Configure Custom actions" and click the Plus sign to add a new action, call it whatever you want and describe it, then in the command box use ```
/home/username/copy.sh %F
```using your username, of course, and in the **Appearance conditions** tab select all six boxes.
That should do it, though you may need to restart thunar.

---

### Post by again? on 2017-06-12
Another option is to install and use the nemo file manager.

Drag and drop the photos folder to your side pane in nemo under **My Computer**.
Click on the "+" in the right click menu to reveal a "Move to" menu item.
Folders shown in the left pane under **My Computer** will be listed as destinations.

---

### Post by ajgreeny on 2017-06-12
Yes, you can do what guber2 suggests in thunar , and probably nautilus, as well, using any bookmarks that you have created, but it can be very useful to be able to drill down in the folders to subfolders using the scripts I use.

---

### Post by again? on 2017-06-12
> **ajgreeny said:**
> Yes, you can do what guber2 suggests in thunar , and probably nautilus, as well, using any bookmarks that you have created, but it can be very useful to be able to drill down in the folders to subfolders using the scripts I use.
This is only possible in nemo as far as I know and is different in that you can move a file directly to a location listed in the right click "Move to" menu without opening a dialog.
It's also possible to browse to a location from the same menu if needed.

---

### Post by ajgreeny on 2017-06-12
> **guber2 said:**
> This is only possible in nemo as far as I know and is different in that you can move a file directly to a location listed in the right click "Move to" menu without opening a dialog.
It's also possible to browse to a location from the same menu if needed.
Thanks for that info.

I have not used nemo so was not aware of the options available and it appeared as if you were just moving files to bookmarked folders.

Good to know!

---

### Post by Strasmus on 2017-06-16
Thanks for that Guber. That actually did the it, as i wasn't looking a permanent "Move to", but more as a temporary solution when cleaning out my (in this case) photo folders.

Much appreciated all the suggestions!

---

