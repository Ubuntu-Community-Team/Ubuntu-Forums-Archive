---
title: "Scrollbar clicking/shift clicking behavior problem"
date: 2020-05-30
forum: General Help
---

### Post by Ralph L on 2020-05-30
I am running Xubuntu 18.04 with the Clearlooks-Phenix theme, but I have the same problem using other themes.  I have some issues with different applications behavior, when clicking on the scrollbar. Libreoffice Writer works best for me.  If I click the scrollbar below the slider, the slider moves down to my cursor and stops.  If I click above the slider, the slider moves up to my cursor and stops.  I would like everything to work this way.
In Firefox if I click on the scrollbar below the slider, the slider moves very rapidly to the bottom of the scrollbar.  It may "hiccup" slightly, when it passes the cursor, but not long enough for me to release the left-click button.  If I shift-click the scrollbar below the slider, the slider stops at the cursor location (like Writer does without the shift).
In Thunar if I click on the scrollbar below the slider, the slider passes the cursor and goes to the bottom of the scrollbar (like Firefox, but as a much slower rate).  Shift-click on the scrollbar behaves the same way as a non-shift click--slider goes to bottom of scrollbar.
As I said above I would like everything to work the way Writer does--particularly Firefox.  It scrolls past the cursor at rip speed--very annoying.
I have tried the Firefox "about:config (ui.scrollToClick=0)" fix and the set "~/.config/gtk-3.0/settings.ini to [Settings] gtk-primary-button-warps-slider=false", and neither worked. [https://unix.stackexchange.com/questions/276005/scrollbar-moves-to-where-i-click](https://unix.stackexchange.com/questions/276005/scrollbar-moves-to-where-i-click) 

Anybody have any other ideas????????

---

### Post by Ralph L on 2020-05-31
I got Firefox to work the way I wanted by going to "about:config" and setting "ui.scrollToClick=1".  I did not realize that I needed to change the type of this parameter from boolian (default) to number by clicking on the trash can.  Firefox now works the way I want, but Thunar still needs fixed.
Any help appreciated.......

---

### Post by Ralph L on 2020-06-01
I forgot to include Thunderbird as an app that autoscrolls past the cursor.  I would like that scrolling to also stop, when it reaches the cursor in the slide trough (the trough click that started the autoscroll).  Like Firefox, Thunderbird has many many parameters in the config editor.  Hopefully one of them has the effect I want, but I don't know which one.

Any help appreciated...

---

### Post by &amp;KyT$0P# on 2020-06-02
> **Ralph L said:**
> I forgot to include Thunderbird as an app that autoscrolls past the cursor.  I would like that scrolling to also stop, when it reaches the cursor in the slide trough (the trough click that started the autoscroll).  Like Firefox, Thunderbird has many many parameters in the config editor.  Hopefully one of them has the effect I want, but I don't know which one.

Any help appreciated...

Try the exact same as you did in Firefox?

---

### Post by Ralph L on 2020-06-06
halogen2:  Thanks for the response.  I appreciate it.  However, Thunderbird about:config does not appear to have a ui.scrollToClick option.  At least I couldn't find it. Any other suggestion??

---

### Post by &amp;KyT$0P# on 2020-06-06
Does it work if you create it?
Right-click > New, select the same type as this pref is in Firefox

---

### Post by Ralph L on 2020-06-07
halogen2:  It worked!!!!!!!  Thank you very much.  I had no idea that one could add new parameters.  

Now I have one more question for you.  Using shift-click or right-click I can get back the old behavior of the slider paging down the screen.  However, the paging is too fast for me to make much use of it (for both Tbird and Firefox).  Do you know of a parameter that will slow that down??

---

### Post by &amp;KyT$0P# on 2020-06-09
Try experimenting with [FONT=Courier New]general.smoothScroll.pages.durationMaxMS[/FONT] and [FONT=Courier New]general.smoothScroll.pages.durationMinMS[/FONT] ?

---

### Post by Ralph L on 2020-06-13
halogen2:  Again thank you for getting back to me.  I tried your suggestion of  experimenting with general.smoothScroll.pages.durationMaxMS and general.smoothScroll.pages.durationMinMS.  I set these to big, small, and even negative numbers.  But no effect on the scrolling speed, when shift clicking on the scrollbar.  In fact I tried changing just about every parameter that started with "general.smoothScroll", but no effect.

---

### Post by Ralph L on 2020-10-27
It turns out that the problem of the slider racing to the bottom of page in Firefox is caused (mostly) by news articles that include a video at the beginning.  The text of the article loads before the video part.  Because the text part is loaded, but not the video, the slider is displayed and is quite long.  So I click on it to scroll the text.  In the meantime the video completes its loading causing the slider to shorten.  So now I am clicking on the slider trough, not the slider.  Sensing this the slider races to the bottom of page (don't know why it moves so fast).  By interchanging click and shift-click as described above, the slider jumps downward but stops at my cursor location, which is usually very close to the top of the trough, and I can slip it back to the top if I want to.
I would still prefer that Firefox slow down it scrolling (when I am clicking on the trough), but the workaround (interchanging click and shift-click behavior) is good enough for now.  Also, the problem is not caused by the ClearLooks Phenix theme.  It happens with all themes.

---

