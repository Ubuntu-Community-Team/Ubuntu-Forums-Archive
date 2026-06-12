---
title: "Don't know what file to use to install a fix to ~/.config/gtk-3.0"
date: 2020-03-04
forum: General Help
---

### Post by Ralph L on 2020-03-04
I am running Xubuntu 18.04, and I am having problems with the Clearlooks-Phenix Theme.  This site ([https://github.com/jpfleury/clearlooks-phenix/issues/41](https://github.com/jpfleury/clearlooks-phenix/issues/41) ) recommends corrective code be installed in ~/.config/gtk-3.0, but it doesn't name the file to be used.  I tried installing it into ~/.config/gtk-3.0/gtk.css , but it didn't work.  I can't find the code's author to question him, but I thought somebody might know the appropriate way to install this type of code:```
/* fixes bug in Clearlooks-Phenix,
 * where clicking rightmost 1px edge of slider
 * does a warp-scrolls instead of grabbing slider
 */
.scrollbar.vertical trough,
scrollbar.vertical trough {
  border-width: 1px 0px 2px 1px;
}
``` Also, the Clearlooks-Phenix theme file (/usr/share/themes/Clearlooks-Phenix/gtk-3.0/) has a gtk.css file in it.  Does this file override ~/.config/gtk-3.0 ?  Should I install the corrective code in /usr/share/themes/Clearlooks-Phenix/gtk-3.0/ .    Any help is appreciated.........

---

### Post by Ralph L on 2020-03-10
Would sure appreciate it if somebody who knows about gtk-3 would give me advice.........

---

### Post by norobro on 2020-03-10
I can't help with your problem, I don't even know what warp-scroll means, but you can test to see if the css file is read by changing the width of some of the borders. Check out this screenshot of .config/gtk-3.0/gtk.css.

As for contacting the code's author, follow the instructions in the following link to find an email address for him. We don't want him to get spammed so I won't post it here. [https://www.sourcecon.com/how-to-find-almost-any-github-users-email-address/](https://www.sourcecon.com/how-to-find-almost-any-github-users-email-address/)

---

### Post by Ralph L on 2020-03-12
norobro

Thank you very much for the response.  You got me thinking in an entirely new direction of experimenting.  Using your test I was able to show that the file ~.config/gtk-3.0/gtk.css was the right file and that I could alter the slide trough with it.  By experimentation I fount that the setting border-width: 0px 0px 0px 2px was better for my use that the setting mentioned in the work around website.  This setting eliminated the problematic narrow strip of slider trough on the right side of the slider.  However, it moved the narrow strip to the left side of the slider.  I think I prefer to have the right side work correctly and the left side to have a problem.  I am going to try this for a while.  Incidentally the first and third px settings are for trough space at the top and bottom of the slider trough.

I also tried experimenting with a number of slider and trough (changing the width of these items) settings in /usr/share/themes/Clearlooks-Phenix/gtk-3.0/gtk-widgets.css, but I couldn't get my changes here to have any affect.  Don't know what I did wrong

Again, thank you

---

### Post by norobro on 2020-03-12
You're welcome.

I don't experience any problems with the clearlooks theme on Ubuntu 19.04. The GTK docs say that they "loosely follow" the css specifications so if they are adhering to the box model you might try adjusting the padding attribute also: ```
.scrollbar.vertical trough,
scrollbar.vertical trough {
  border-width: 1px 0px 2px 1px;
  padding: 0px 0px 0px 0px;
}
```

[https://developer.gnome.org/gtk3/stable/chap-css-overview.html](https://developer.gnome.org/gtk3/stable/chap-css-overview.html)

---

### Post by Ralph L on 2020-03-14
norobro
Again, thanks for your response!!!!!!

I tried your suggested settings for border-width and padding, but with no luck. When I clicked on the narrow band just to the right of the slider, it took off for the bottom of the page at warp-speed.  This happens only with FIREFOX, as near as I can tell.   I don't know what "padding" really is, but I tried setting it to a width of 10 and there was an area on either side of the trough.  However, clicking in this padding area had the same effect as clicking in the trough.  The slider took off to the bottom of  page.  So, yes, I want 0 padding as you specified, but it didn't fix the problem.  So far the only way I have been able to eliminate the narrow band of sensitivity to the right of the slider is by "border-width: 0px 0px 0px 2px;".  The extra border width (2px rather than 1px or 0px) to the LEFT seems to take away the sensitive area to the RIGHT (go figure),but leaves a sensitive space to the left (bad).  However, this isn't as much of a problem for me as is having the sensitive space to the right.

Have any other ideas..........

---

### Post by u666sa on 2020-03-15
Do you have XFCE 4.12 or 4.14??

[COLOR=#b22222]xfce-about [/COLOR]
&
[COLOR=#b22222]xfce-panel --version[/COLOR]

If it is 4.12 then the file is [COLOR=#333333][FONT=Verdana]~/.gtkrc-2.0

If it is 4.14 then the file is gtk.css inside gtk 3 folder as you mentioned. 

You could also have a badly upgraded XFCE, if you tried to upgrade it and it still says 4.12 in xfce-about. Then neither option will work.

I wrote a guide on how to update XFCE 4.14.[/FONT][/COLOR][https://ubuntuforums.org/showthread.php?t=2438495](https://ubuntuforums.org/showthread.php?t=2438495)

---

### Post by Ralph L on 2020-03-15
u666sa
Thanks for the response.  I appreciate it.  Using xfce4-panel --version, I see that I have xfce4-panel 4.12.2.  However, as implied in the various experiments that I did above (prompted by norobro), I found that making changes to ~.config/gtk-3.0/gtk.css resulted in visible changes to the slider trough that appeared on my screen.  So using gtk-3.0 seems to be correct.  The reason that I didn't originally see the changes (prompting the original question) was that the changes were too small to be seen on the screen.  Larger changes as suggested by norobro showed up fine.

However as indicated, the original work around suggested in the website [https://github.com/jpfleury/clearlooks-phenix/issues/41](https://github.com/jpfleury/clearlooks-phenix/issues/41) did not work.  In fact nothing I tried really solved the problem of the slider warp-speeding to the bottom of page, when the narrow band just to the right of the slider was accidentally clicked.  I found a better work around (explained above), but it doesn't really solve the original problem.

Again, thanks for your response.

---

