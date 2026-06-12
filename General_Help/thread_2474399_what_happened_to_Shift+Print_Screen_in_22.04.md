---
title: "what happened to Shift+Print Screen in 22.04?"
date: 2022-04-28
forum: General Help
---

### Post by ronjjjg8885 on 2022-04-28
it take a whole screen screenshot.

i want it like in earlier versions where this key combination will allow to make what i want to shot very easily....

possible?

---

### Post by deadflowr on 2022-04-28
The Print button by itself is now interactive which allows selecting which screenshot type you want, either window, area, or full screen.
Not sure if it does it for everyone, but it also saves autmatically it to ~/Pictures/Screenshots for me.

I do not know if it's possible to change the settings.
As I have not looked hard enough.

But I kind of like the new setup for it, since it also integrates a screencast option feature too,
which kind of cool.

I guess if you want you can rearrange the shortcut keybindings.
If you go to Settings Keyboard, scroll down to View and Custom Shortcuts, then open the Screenshot item it'll show the current shortcuts for screenshots.
If you click on any of those items it will open a popup window allowing you to set a new shortcut.

---

### Post by coffeecat on 2022-04-28
As deadflowr says, the Print Screen key alone brings up a little interactive window - described here [https://9to5linux.com/first-look-at-gnome-42s-built-in-screenshot-and-screencast-feature](https://9to5linux.com/first-look-at-gnome-42s-built-in-screenshot-and-screencast-feature) - from which you can choose full screen, selection or active window, and whether or not you want a screenshot or screencast.

On my 22.04, Shift + Printscreen gives me a full screen screenshot with no interactive window, and Alt + Printscreen the active window just as with the old screenshot utility.

---

### Post by ajgreeny on 2022-04-28
I don't use Ubuntu but have been on Xubuntu for many years now.

Using xfce4-screenshooter and keyboard shortcuts to the commands shown, I can choose to print-screen either fullscreen, (***xfce4-screenshooter -f***) active window, (***xfce4-screenshooter -w***) or area defined with the mouse (***xfce4-screenshooter -r***).  All three commands bring up a dialogue asking if I want to save the image, copy it to clipboard, open with a third party application or Host on Imgur.

Clever, dead simple and very easy to setup.

---

### Post by vanadium on 2022-04-29
> **coffeecat said:**
> 
On my 22.04, Shift + Printscreen gives me a full screen screenshot with no interactive window, and Alt + Printscreen the active window just as with the old screenshot utility.

This is the answer. Former "PrtScr" now is "Shift+Prtscr". The difference is that a screenshot now automatically is saved *both* to the clipboard and a file. Formerly, you had to add Ctrl to save to the clipboard instead of to a file (and decide ahead of taking the screenshot which output you wanted.

I find the current implementation very sleek and very well designed.

---

### Post by mIk3_08 on 2022-04-29
> **ronjjjg8885 said:**
> it take a whole screen screenshot.
i want it like in earlier versions where this key combination will allow to make what i want to shot very easily....
possible? In my case, print screen uses function key then print screen button to take screenshot the whole desktop display but when selecting area to grab i usually use screenshot Ubuntu app so I can easily grab the area to be screenshot. regards and cheers.

---

### Post by ronjjjg8885 on 2022-04-30
i've just discovered you can draw a selection with the mouse like in the past...

one more thing. i want to change the screenshots directory to be in 'pictures' and not in a folder inside of pictures....

how do i change this path?

---

### Post by mIk3_08 on 2022-05-01
> **ronjjjg8885 said:**
> i've just discovered you can draw a selection with the mouse like in the past...
one more thing. i want to change the screenshots directory to be in 'pictures' and not in a folder inside of pictures....
how do i change this path?
You can change the directory by selecting "other.." instead of pictures. just click the down arrow button then select the  "other..." then select which folder you want to save your screenshot. cheers. see image below:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290365&stc=1[/IMG]

---

