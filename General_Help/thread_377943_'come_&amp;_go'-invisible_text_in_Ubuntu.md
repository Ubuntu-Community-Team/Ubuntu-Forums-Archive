---
title: "'come &amp; go'-invisible text in Ubuntu"
date: 2007-03-06
forum: General Help
---

### Post by -Woodrow- on 2007-03-06
hi,

I've got a little problem with my Ubuntu Dapper installation as the text in my browser (opera) and also the text of the menubars and buttons outside of opera has become somewhat invisible. If I select the text (in opera) it becomes visible, links work with just mouseover/hovering over them. Sometimes the returned text disappears once more, when the window regains focus after switching between several windows.

These screenshots probably help me point out the problem: [Selected Text](http://xs413.xs.to/xs413/07102/visible_text.png), [Also Buttons](http://xs413.xs.to/xs413/07102/also_buttons.png)

Before this happened I fiddled around with XGL using [this tutorial](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-dapper/), then entering
"$ compiz --replace gconf &
$ gtk-window-decorator --replace &"
as described [here](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz). And even before that I created the files "/usr/bin/startxgl.sh" and "/usr/share/xsessions/xgl.desktop" following [these instructions](https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29).
I tried to backtrack my steps, so I removed all packages I have installed for XGL via "sudo aptitude remove ...", those two files mentioned above, did reboot and update, upgrade and dist-upgrade everything but to no avail.

Opera has the biggest trouble, but other programs just as well fail to display some texts, like Thunderbird, Gedit, Firefox. I wonder if this has something to do with the fonts or desktop-drawing or something.

oh yes, my standard session is gnome.

I hope this is repairable without reinstalling ubuntu - can someone help me with this one?

---

### Post by -Woodrow- on 2007-03-20
> **-Woodrow- said:**
> I hope this is repairable without reinstalling ubuntu - can someone help me with this one?
well, actually it is!
just go to /etc/X11/xorg.conf and add/change this value in the section of the nvicia-card:
Option "RenderAccel" "false"

piece o' cake!

---

