---
title: "Yes, I have searched the forums...."
date: 2006-12-02
forum: General Help
---

### Post by gila_monster on 2006-12-02
...but it seems that certain sites with (I'm guessing) Flash (mayitsnamebecursed) are still crashing Firefox 2 and Opera on my Kubuntu Edgy box.

I have added

export XLIB_SKIP_ARGB_VISUALS=1

to /etc/firefox/firefoxrc. I have set my default depth to 24 in /etc/X11/xorg.conf. Both of these seemed to help, but both FF2 and Opera lock up on certain sites. (Not always. I think it depends on certain Flash ads on some sites.)

I am at a loss for what to try next. I have the latest Flash 9 (installed from repository this morning), and that changed nothing. Is there anything else I should be checking?

Thanks much.

gila

---

### Post by gila_monster on 2006-12-03
Okay, I guess I should have checked the Adobe site first. They say that

"The plugin does not currently work in Opera browsers. We are working with Opera on this issue."

It works most of the time, but apparently I should lower my expectations. They also claim that Flash 9 is supported only for Firefox 1.5.x, and I'm guessing that if the items I tried above don't always work, I'll just have to wait for beta 3 or the final release and hope for the best.

Thanks to those who read the message and gave it a little thought.

---

