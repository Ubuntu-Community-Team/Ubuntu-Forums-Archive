---
title: "Send To not in right click menu"
date: 2014-08-10
forum: General Help
---

### Post by rickm1945 on 2014-08-10
I was reading about sending files in Ubuntu, and it said to select file, right click and select "Send To" and then select options from the menu. I don't have the "Send To" when I right click. I am using Ubuntu 14.04 LTS. Any help will be much appreciated.

---

### Post by ajgreeny on 2014-08-10
I use Xubuntu and thunar and in that I use a script that I point to with a thunar custom-actions command.

I know there is a similar nautilus-scripts folder somewhere in your /home to which you can add such things, but I'm not quite sure of the necessary details; this script may give you some clues of what might be helpful to you if appropriately amended for nautilus.
```
#!/bin/sh
[ 0 -eq $# ] && exit
dst=$(zenity --title='Where to move' --file-selection --directory) || exit
/bin/mv -- "$@" "$dst"
```

---

### Post by mc4man on 2014-08-10
Depends on what you want to do & what's installed.
Locally the context menu has copy to & move to options

As far as 'send to' it is not a direct option in the context menu but is exposed thru the mail... option if nautilus-send-to package is installed. The options within that send-to pop up depend on what's installed.
screen 1 show 3 packages
screen 2 the send to pop up from the context menu email.. option 
screen 3 with all 3 of the highlighted packages installed the send to 'Destination' dropdown

---

### Post by rickm1945 on 2014-08-10
Thanks, I looked in the Synaptic Package Manager, it shows all three as being installed. So I will mark this thread Solved.

---

