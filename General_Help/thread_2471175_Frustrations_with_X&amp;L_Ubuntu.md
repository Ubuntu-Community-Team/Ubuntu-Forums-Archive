---
title: "Frustrations with X&amp;L Ubuntu"
date: 2022-01-22
forum: General Help
---

### Post by Quarkrad on 2022-01-22
A neighbour has a low spec machine and I'm going to show her ubuntu as I keep having to re-build windows (10) for her.  I have emulated her machine as far as possible on a ubuntu mate mule at home but have been playing this afternoon with both xubuntu and lubuntu.  Moving icons within a panel has proved frustrating to say the least.   I want a single panel at the bottom and this is easy, as is placing launcher icons on the panel.   However, in ubuntu mate you right click on an icon and select *move*, then move and place the icon anywhere in the panel.  Assuming this simple act is possible I have yet to find out how to do it. Is it possible in either lubuntu or xubuntu to be able to place icon/launches anywhere in the panel?  (On xubuntu I can move to the extreme left or extreme right but not 'where I like').  Thanks.

---

### Post by &amp;KyT$0P# on 2022-01-22
In Xubuntu: right-click panel > Panel > Panel Preferences > Items, you can drag&drop the list to change the order.

---

### Post by KBar on 2022-01-22
The above, and you can also right-click on any panel item, select *Move* and place it anywhere you like, including in a different panel.

---

### Post by Quarkrad on 2022-01-22
**halogen2**  yes that is correct, but it seems you can only change the order as they are group together on the left.  E.g. if I have in the left hand corner, in order, *Applications Menu, File Manager, Firefox,  Fonts, Notes*   I can change the order to:  *Applications Menu, File Manager, Fonts, Notes, Firefox.*   But if I want  *Applications Menu, File Manager, Fonts, Notes* all grouped together in the left hand corner and *Firefox* in the middle of the panel how do I do that?  In ubuntu mate you can move/drag icons/launchers where you like in the panel with whatever gap between them.

**KBar ** How do you do that?  Within the same panel how do move a launcher to say one in the left corner, another in the right corner and two others in random positions? Say 27% from the left and 72% from the left.  Xubuntu will no let me move the icons to any position I wish. Only next to an existing launcher.

---

### Post by Quarkrad on 2022-01-22
Here is my problem.  Created a panel on the Desktop (xubuntu) and added a launcher.  Right clicked to move it to the right - as I move the launcher to the right a red line appears to the right of the launcher.  I cannot move this launcher to the right - the red line stops me.   If I have 8 launchers I can change the order of them but I cannot move any launcher past the last launcher - the red appears and stop me.  Ubuntu Mate does not have this red line - you can move any launcher anywhere.

---

### Post by &amp;KyT$0P# on 2022-01-22
> **Quarkrad said:**
> if I want  *Applications Menu, File Manager, Fonts, Notes* all grouped together in the left hand corner and *Firefox* in the middle of the panel how do I do that?

You can add Separator, then right-click > Properties & click "Expand", then it will fill the width of the panel between its left and its right.  In this case put one of these to each side of the Firefox launcher.

---

### Post by Holger_Gehrke on 2022-01-22
You can't really put things in random positions on panels in XFCE but you can use separators. These can be inserted in the items dialog and can be set to be transparent / invisible and to take up all available free space. So if you want three groups of items (left, centre, right) you put separators in between them and set them to take that space.

Holger

---

### Post by GhX6GZMB on 2022-01-22
In Lubuntu, just drag 'n drop; I can arrange my desktop any way I want. I can also lock them in place. What's the problem?

---

### Post by ajgreeny on 2022-01-22
As Holger says, in Xfce, Xubuntu, the left and right hand group of applet or launcher icons are separated by a separator which is expanded to fill the space between the two groups.

It is not possible to place an icon/applet in that expanded space and without the separator all the icons would be in a single group at the left hand end of the panel.
You can not drop and icon anywhere you want, but you can right click on the icon you want to move and take it left or right, from left group to right group or even from panel to panel if you have more than one panel on your desktop as I do.

My second panel contains only launchers for applications which many or most users place all over their desktop; I don't like that as I fill my desktop with two conky displays of information; time and date in one and system information in the second.

You can if you wish use more than one expanded separator and have a central group of icons/launchers, or even a single one if that's what you want.

---

### Post by GhX6GZMB on 2022-01-22
> **ajgreeny said:**
> 
It is not possible to place an icon/applet in that expanded space and without the separator all the icons would be in a single group at the left hand end of the panel.
You can not drop and icon anywhere you want, but you can right click on the icon you want to move and take it left or right, from left group to right group or even from panel to panel if you have more than one panel on your desktop as I do.

My second panel contains only launchers for applications which many or most users place all over their desktop; I don't like that as I fill my desktop with two conky displays of information; time and date in one and system information in the second.

You can if you wish use more than one expanded separator and have a central group of icons/launchers, or even a single one if that's what you want.

Doesn't sound very attractive to normal users nor to me.

---

### Post by guiverc on 2022-01-22
As ml9104 has already said; you can drag & drop (*the mouse-pointer will change when you do it right, going green(+) when you can drop & red(-) when you cannot though theme being used at the time does impact how it shows*..)

You didn't provide release details, so I'll provide the manual for the *latest* stable release; ie. link is for 21.10  (*adjust if you're using an older release - best if you're specific with release details as then we can provide links that apply for your release*)

[https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html)

---

### Post by Quarkrad on 2022-01-23
Perhaps this is me having used ubuntu mate for some years and become use to the way it works.  I added two separators and expanded them and they jumped to positions 1 and 2. If I right click on them I cannot move them either to the left or the right(?) - they appear fixed.  Launcher 3 is mid way between 1 and 2.  How do I move 3 to position 4?  Or if I change my mind in a months time say 5mm to the right of 4? (Fresh install of xubuntu 20.04 - fully up to date).

---

### Post by KBar on 2022-01-23
For such fine-grained placement of elements, I'd resort to CSS. If that launcher had some internal ID, say 21, this is how one could change its position in the panel:```
#launcher-21 > box {
  margin-left: -150px;
  margin-right: 150px;
}
```

Here is how it looks after:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289877&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289878&stc=1[/IMG]

Custom CSS rules are defined in *$HOME/.config/gtk-3.0/gtk.css*. If that file doesn't exist, it can simply be created. 

To find out a launcher's internal ID, hover over its entry in the items list like so:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289879&stc=1[/IMG]



If this route is not too attractive, it should also be possible to fill up the entire panel with however many transparent separators without expanding them, and then move individual items. One separator is 6px wide, if I recall correctly.

---

### Post by Quarkrad on 2022-01-23
**KBar**  Thank you for your detailed response. I have played with the CSS rules and the multiple separators and can now achieve what I want - brilliant.

---

