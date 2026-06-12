---
title: "How do I get up/down scrollbar buttons in Lubuntu?"
date: 2013-06-08
forum: General Help
---

### Post by mivadar on 2013-06-08
Remember those arrows at the ends of vertical scrollbars for scrolling up and down? I would like those on my Lubuntu system. It's a pain without them, particularly when using a laptop with no external mouse.
(Using arrow keys on the keyboard is not a solution - in several programs either it does something different, or defeats what I want to do. e.g. Trying to select multiple items in a file manager by Ctrl+click, can scroll down by scroll-bar, but going up/down by arrow keys de-selects items - scrolling by touchpad without up/down arrow buttons drags me potentially dozens of files off from where I want to be.)

As I understand overlay-scrollbar is something different and is not the subject of my question. So I don't think this is a duplicate of How do I disable overlay scrollbars?. I see the problem in every single program in lubuntu that integrates in LXDE (LXTerminal, gimp, filezilla, PCManFM file-manager, emacs, chromium, etc. ) - visible scrollbar but no arrow buttons at either end.
So far the only exceptions (where I have little minus signs at the end of scroll-bars that function like the arrows) are firefox, thunderbird and libreoffice. 
Its the buttons I want back. I followed the instructions to the supposed duplicate overlay-scrollbar and they had no effect after a restart.

---

### Post by Dennis N on 2013-06-08
The arrows on the scrollbar come with the theme in use. Lubuntu defult theme doesn't have the arrows. Clearlooks is an example of a theme that does have  them.

---

### Post by vasa1 on 2013-06-08
And you can find Clearlooks in the Widgets tab in Menu, Preferences, Customize Look and Feel.

---

### Post by mivadar on 2013-06-09
Thank You!

I'll try the clearlook theme.

In the meantime I was playing around and found another solution:

for programs that use gtk 3:

change **/usr/share/themes/Lubuntu-default/gtk-3.0/gtk-widgets.css**

    -GtkScrollbar-has-backward-stepper: 0;   *to*     -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 0;   *to *    -GtkScrollbar-has-forward-stepper: 1;

in the section:

**************
 * Scrollbars *
 **************/

.scrollbar {
    -GtkRange-slider-width:     9;
    -GtkRange-stepper-size:     0;
    -GtkRange-stepper-spacing:  0;
    -GtkRange-trough-border:    0;

[B]    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;[/B]
    
    -GtkScrollbar-min-slider-length: 30;	
}

for programs that use gtk 2:

change **/usr/share/themes/Lubuntu-default/gtk-2.0/scrollbar.rc**

    GtkRange::stepper-size = 0   *to*     GtkRange::stepper-size = 8

in the section:

style "scrollbar" 
{
	GtkRange::slider-width = 8
	GtkRange::stepper-size = 8
	GtkCheckButtonClass::indicator-size = 14
	GtkRadioButtonClass::indicator-size = 14
		
	engine "pixmap" 
	{

etc.

---

