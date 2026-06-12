---
title: "Application menus require moving almost directly right to access or they disappear"
date: 2014-08-16
forum: General Help
---

### Post by Rev2010 on 2014-08-16
**EDIT - including screen capture to show what I am referring to.

I think this might be my last question as I've sorted out everything else I could think of so far in my upgrade from 12.04 to 14.04. So, the last thing I'd like to tackle is it seems now when I click the Applications menu and quickly move my mouse up or down and to the right with slightly too great an angle the menu just vanishes and I have to move back to the left and do it again and more accurately to select the items on the right. In other words, if I click Applications -> System Tools then move my mouse over to the right with anything more then say 10 degrees upward motion the menu closes. I have to literally move nearly directly right THEN up and it's a real nuisance since I've never had this issue before. It makes quick motion a pain. Any way to change this behaviour? I tried Googling various phrases but it's so hard to define. I've tried "Menu popup duration" to maybe set it longer, and various other terms, but nothing yeilds any useable results. Thanks.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255595&d=1408392993[/IMG]


Rev.

---

### Post by mike225 on 2014-08-16
unity-control-center
Appearance > Behavior

---

### Post by Rev2010 on 2014-08-16
Sorry, should've been more specific. I'm using Gnome Flashback.


Rev.

---

### Post by Rev2010 on 2014-08-16
Anyone? As is currently it makes working with the menus rather annoying. I verified on my wife's 12.04 laptop this doesn't occur. It's not a Compiz thing as it does this under Metacity too. I'm thinking it's a Gnome setting. Probably something to do with menu popup response/hold times. Normally when I used to click Applications -> System Tools then move the mouse diagonally up to the right and click on Administration with no issues. Now if I go diagonally up the menu disappears. I have to go straight right THEN up.


Rev.

---

### Post by Rev2010 on 2014-08-18
I've updated the original post to show a screen capture of the issue. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255595&d=1408392993[/IMG]

---

### Post by CantankRus on 2014-08-18
Before in gnome2 you could control this in a ~/.gtkrc-2.0 file with an entry **gtk-menu-popup-delay = 0**
This would make the menu react without delay.
Think there is also gtk-menu-popdown-delay
Here's a link to an old post [http://community.linuxmint.com/tutorial/view/209](http://community.linuxmint.com/tutorial/view/209)

I don't know how this works with gnome3 and the flashback version of gnome-panel though.

---

### Post by Rev2010 on 2014-08-19
I'd tried the popup delay setting before and it had no affect. Looking at the link you provided though it looks more like gtk-menu-popdown-delay would be the setting, since I want the menu to stay up longer. However, another link states, "
 GtkSettings:gtk-menu-popdown-delay has been deprecated since version 3.10 and should not be used in newly-written code.
 This setting is ignored."

So it appears that likely wouldn't work either? It's killing me, this is the last tweak I need to make to Ubuntu 14 to be golden, I've gotten every other thing where I want it. This issue is livable of course, but I do often have to retry selecting menu items since I've always been able to just diagonal up to selections. As mentioned, I reverified this as well on my wife's 12.04 laptop, it doesn't experience this issue at all. I put Ubuntu 14 on my work machine as well but am out on PTO so I can't check to see if this exists on that machine also until Thursday.

 


Rev.

---

### Post by CantankRus on 2014-08-19
Don't know if your familiar with [**_[COLOR="#B22222"]ClassicMenu Indicator[/COLOR]_**]("http://www.florian-diesch.de/software/classicmenu-indicator/") 
Was made for unity to mimic the old applications menu.

I was just looking at this and it seems to behave how you want.
Could get rid the of the main menu bar and just use the classicmenu-indicator.
Will only show in the **indicator complete applet** though.
Think its in the repos in 14.04 or use the link above for the latest deb.

---

### Post by Rev2010 on 2014-08-19
Just tried the Classic menu and same results, menus disappear when trying to move diagonally to them. I'm really thinking this is a Gnome setting. Just don't know what the heck to change.


Rev.

---

### Post by Rev2010 on 2014-08-28
Bumping this one last time in hopes someone knows what setting needs to be changed.

---

