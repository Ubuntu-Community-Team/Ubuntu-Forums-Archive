---
title: "how to remove ALL notifications. XFCE / (xubuntu)"
date: 2015-02-28
forum: General Help
---

### Post by aspidistra on 2015-02-28
the main, larger notificaitons for brightness indicator, etc have 
been removed

notify-osd has been removed

other things

what removes these?  the mouse is hovering over a button
its giving me a b lack recktangle of text what the button is, everywhere
i put pointer over my clock applet - digital clock - I get two clocks
I ge terminal descriptions in applets - I get description of every button

these (below) are the notifications I am talking about - how to remove please?
I want them GONE

[http://i.imgur.com/o1RO8ED.png](http://i.imgur.com/o1RO8ED.png)

---

### Post by kerry_s on 2015-02-28
those are tool tips

[http://ubuntuforums.org/showthread.php?t=1516052](http://ubuntuforums.org/showthread.php?t=1516052)

---

### Post by pmi2 on 2015-02-28
I think you may want the fix specific to XFCE, like this, or similar:

[http://askubuntu.com/questions/502217/xfce-disabling-tooltips](http://askubuntu.com/questions/502217/xfce-disabling-tooltips)

---

### Post by aspidistra on 2015-03-05
thanks 

"how to remove all tooltips"  re site ^

""""""
[COLOR=#333333][FONT=Lucida Grande]I got the answer on #xfce on freenode and here: [/FONT][/COLOR][http://forum.xfce.org/index.php?topic=2651.0](http://forum.xfce.org/index.php?topic=2651.0)
[COLOR=#333333][FONT=Lucida Grande]So, I did this:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]created a file called in /home called .gtkrc-2.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]all that is in the file is this:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]gtk-enable-tooltips = 0[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]It works, no more tooltips.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]It is universal, so all apps lose their tooltips. (including losing the date pop-up if you mouse over your panel clock)[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I was also warned if I use desktop icons, drag and drop will not work after doing this. Not a big deal.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]The devs consider this a bug, apparently. I didn't take the time to find the bug report, though.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]To enable tooltips, just change the 0 to a 1 in the file or just delete .gtkrc-2.0 file."[/FONT][/COLOR]

---

### Post by kerry_s on 2015-03-05
that was answer #9 on the link i posted.

i might try that, but i'm using elementary os freya(beta), which is moving towards gtk3. i am using xfce4-panel in place of wingpanel though, but i already turn off tool tips in the launchers, except the 1's i want to show.

---

