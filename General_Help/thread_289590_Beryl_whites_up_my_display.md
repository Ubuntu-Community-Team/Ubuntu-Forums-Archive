---
title: "Beryl whites up my display"
date: 2006-10-31
forum: General Help
---

### Post by hk_2999 on 2006-10-31
I have an nvidia card and been using Beryl for some time. But today, I just get this:

[IMG]http://www.geocities.com/login99ph2003/screenshot.png[/IMG]

My panel just became a block of white, and the windows I have sometimes become became a blank white window with a titlebar on it. Sometimes the title bar gets the problem, and becomes a blank title bar. It's really creepy...

Does anyone know any workaround to this problem. Im using AIGLX.

---

### Post by louis_nichols on 2006-10-31
> **hk_2999 said:**
> I have an nvidia card and been using Beryl for some time. But today, I just get this:


My panel just became a block of white, and the windows I have sometimes become became a blank white window with a titlebar on it. Sometimes the title bar gets the problem, and becomes a blank title bar. It's really creepy...

Does anyone know any workaround to this problem. Im using AIGLX.


I had this exact problem a while ago. The scree was just like that right after installing compiz. But it went away on it's own after a reboot. Maybe it's your case, too...

---

### Post by hk_2999 on 2006-10-31
> **louis_nichols said:**
> I had this exact problem a while ago. The scree was just like that right after installing compiz. But it went away on it's own after a reboot. Maybe it's your case, too...

I found out the problem is that I'm loading Xgl on boot. I forgoy edgy has AIGLX built-in. Not loading startxgl.sh at boot solved my problem.

---

