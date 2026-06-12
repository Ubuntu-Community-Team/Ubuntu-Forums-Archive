---
title: "Gyac-E tray icon not shown correctly in Moomex-theme"
date: 2008-05-23
forum: General Help
---

### Post by realthor on 2008-05-23
Hi, using Hardy Heron and Moomex-theme here. The tray icons of many apps eg Gyach-E, gnome update notifier etc appear displaced 2-3 pixels below the upper limit of the panel.It's not very disturbing but it's an annoyance. I am convinced it's something with the theme but as many of you have already seen this if using moomex theme and  perhaps someone knows a workaround...perhaps how to modify the .gtrk file to solve this.

In the print-screen below i raised the dim of the panel so that also the bottom displacement is visible...usually the panel height is 33 pixels...less is not possible because of how the theme was built (one has to modify the gtrk to ba able to do this).

---

### Post by moomex on 2008-05-23
Try this workaround,

1) Type in Terminal:
gedit $HOME/.themes/Moomex/gtk-2.0/gtkrc

2) Remove or comment these lines:
class "*Tray*"		style "panel-moomex"

class "*tray*"		style "panel-moomex"

widget_class "*Tray*"	style "panel-moomex"

widget_class "*tray*"	style "panel-moomex"


I will update this theme soon, with new features and bugfixes. :)


P.S.: This bug has been fixed in the Moomex-Ultimatum Themes.

---

### Post by moomex on 2008-05-23
> **realthor said:**
> 
usually the panel height is 33 pixels...less is not possible because of how the theme was built (one has to modify the gtrk to ba able to do this).

To make the panel size less than the 33px you have to edit the gtkrc file. Type in Terminal:
gedit $HOME/.themes/moomex/gtk-2.0/gtkrc

Comment this line under style "panel-moomex"
GtkWidget::focus_padding = 7

I believe this is a feature not a bug. This feature will set the optimum panel size(33px) automatically.

---

### Post by realthor on 2008-05-23
Yes, I wasn't complaining about the 33 px width only about some tray icons displaced like you can see in the attachement. There are not so many until now i have found only gyache and system update to behave like this.

I will surely wait for an updated feature-full theme ...keep up.

---

### Post by loell on 2008-05-23
in gyache-improved you can also uncheck the **attach libnotify (pop up) system to tray** on **setup** --> **options**

---

### Post by realthor on 2008-05-24
that might be right but there are lots of tray icons that behave the same...like transmission's tray icon and more but I can't remmember now.

Here's another pic...seems that this theme does something wrong with tray icons and it's shame cause for me is the most elegant theme i've seen so far.

Moomex, perhaps that new version you were talking about will see daylight VERY soon? :P

---

### Post by moomex on 2008-05-24
Can you please install this theme and report whether or not the same problem still exists?

[http://gnome-look.org/content/show.php/show.php?content=72600]("http://gnome-look.org/content/show.php/show.php?content=72600")

This bug has been fixed for a quite some time in Moomex-Ultimatum. However, I haven't yet included the bugfix in the original Moomex-Theme.

---

### Post by realthor on 2008-05-24
Yes, in ultimatum the issue is not any more. So i hope you'll correct this one too as ultimatum is too black for me and there is wayy too much contrast between the black meny/everything and white backgrounds in open office, web pages, filezilla etc.

I like though though very much the panel items graphics when moused-over. Very slick and elegant. How can I make that in moomex-theme?


Ahh, one more thing...some firefox fonts (the ones when you login in ubuntu forums for example) and open office calc cells are almost white (very white grey) and it's very difficult to see them. I have attached two pictures so u can see.

BR

---

