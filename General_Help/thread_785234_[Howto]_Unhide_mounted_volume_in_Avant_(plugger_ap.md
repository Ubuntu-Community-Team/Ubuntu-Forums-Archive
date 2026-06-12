---
title: "[Howto] Unhide mounted volume in Avant (plugger applet)"
date: 2008-05-07
forum: General Help
---

### Post by dannyking on 2008-05-07
Hello,

If you have hidden a mounted volume from the plugger applet in your avn dock and want to get it back, follow these steps:

1. load up **gconf-editor** (in a terminal or using alt+f2)
[B]
2. Be careful not to change anything else except what I mention here -- you might break something![/B]

3. Find your way to **apps>avant-window-navigator>applets>stacks** and you will see a list of volumes which have been previously mounted.

4. Click on each one and find out which is the volume you want to un-hide (the title will show on the right)

5. When you find it, you'll notice there is a "**hide_volume**" value. You need to **right click on that value and click "unset key"**.

**6. Please note, just un-ticking it without un-setting it will not do anything!**

7. Now you need to **unmount your mounted volume** (if it's already mounted) So for a usb stick, unplug it.

8. Then we need to **restart avn**. type "**killall avant-window-navigator**" in the alt+f2 dialog and it'll close avn. To start it again, type "**avant-window-navigator**" in alt+f2.

It should show up there the next time you attach your device. If not, you need to unmount it properly using nautilus or restart your computer if it's easier. Hope that helps!

---

### Post by xXZeroXx on 2008-08-31
Thanks, I didn't know how to show it :lolflag:

---

### Post by sudhirnair on 2009-10-30
Thanks! I was going nuts trying to unhide this thing :)

---

