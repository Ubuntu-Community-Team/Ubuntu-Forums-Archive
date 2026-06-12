---
title: "help changing font color!"
date: 2006-10-30
forum: General Help
---

### Post by jnev on 2006-10-30
ok, this is a really stupid question, I'm cursing myself for not being able to figure this one out...

anyways, I was playing with the desktop background and stuff, and made it black, but now I can't seem to find a way to change the color of the fonts in the menu bar and the clock because the font is black on a black wallpaper. I know there's a way to change it to white, I just can't find it. help anyone?

here's a screenshot so you can see what I'm talking about..

[IMG]http://img.photobucket.com/albums/v304/jnev_89/Screenshot-1.png[/IMG]


thanks

---

### Post by autocrosser on 2006-10-31
If you don't know it--it's not a stupid question--I've only seen stupid answers;)---The way I've changed font colors is by modifying a theme or creating a custom .gtkrc-2.0 file--there are several ways to change things--I'll put a theme of mine that changes almost everything blue--there is not a wealth of info on the net to modify themes, but I can point you ways if you are interested.....

---

### Post by jnev on 2006-10-31
thanks for the reply. where can I find the themes that are already installed on my system so that I can modify them?

thanks

---

### Post by JLB on 2006-10-31
here ya go. copy this to your text editor, save it to your home directory as .gtkrc-2.0  (please note the DOT in the front of the file name) and then ```
ALT-F2
``` for a run dialog. Type in  ```
killall gnome-panel
```   and enjoy the white fonts. I (hopefully) have added an attachment. just replace the DOT in the filename with a period and drop the .txt suffix.


```

style "panel"
{
 fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

---

### Post by autocrosser on 2006-10-31
Ok--We've shown both ways to mod--your themes are either in /home/<your home>/.themes or in /usr/share/themes. What I do is find a theme that I like parts of & change the parts I don't--you can copy/paste from /user/share/themes to your desktop without disturbing your "stock" themes--make sure that in Nautitlus you have ticked "hidden filles are visible" --you can also look at gnome look.org for more themes. And a google search for gtkrc-2.0 will turn up some interesting things8)

---

### Post by jnev on 2006-10-31
thanks a ton to both of you. I really appreciate the help.

---

### Post by PfD on 2007-01-17
Maybe you could tell a way to go back to black font after that?:mrgreen:  Thanx.

---

### Post by d_xtremw on 2007-06-25
i know this thread is dead but im having some serious trouble with my fonts. i also have a black theme and on ym desktop all the fonts are black by default. also in the text editor page the bacground is black. can anyone help me?:(

---

