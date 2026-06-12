---
title: "sudo: command not found"
date: 2006-12-16
forum: General Help
---

### Post by zappa420 on 2006-12-16
Hey all,

My friends dell laptop is running edgy (I assimilated another windoze user) with kde as the default desktop.  Everything has been great 'till a few days ago when she calls me and says her internet is not working. She has internet troubles before so I just tell her to sudo ifdown/ifup and shes back surfing again.  This last time I tell her to sudo ifdown and she tells me (over the phone I haven't seen it in person): command not found.  I spell it out for her and low and behold its command not found.  I have change directories and confirm for me that ifdown is still there.  I have her type in ifdown and it works but alas you need root privileges.  So knowing that ifdown is there I have her type sudo ifdown again and it's still coming up 'command not found."  So I have her try sudo -i and sudo -s by themselves and it says command not found.  Mind you it is asking for her password before it outputs "command not found." I have her echo $PATH as someone suggested and it seemed a little short, so, I had her change her $PATH with: export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games.  That did not help.  It's still "command not found."  :confused: :confused: 

So anyone have any idea why sudo is seemingly broken?  Anyone have any ideas on how she might have done this in the first place.   I'm lost as to what to do.  I'm hoping I can help her over the phone rather than spending my Sunday tommorrow reinstalling Edgy.

Oh yeah... sudo su didn't work for me and theres no root account so su doesn't work I guess.

Thanks everyone.

Zappa

---

### Post by taurus on 2006-12-16
Ask her what groups she belongs to...

```
id
```
She needs to be on both adm & admin before you can run the sudo command...

---

### Post by zappa420 on 2006-12-16
I can't confirm it at the moment as shes not picking up the phone.  But she's using the original account setup at installation time.   I don't think she does anything besides listen to music, email, use myspace and surf the web.  So I can't imagine her somehow changing her group.  I will will check as soon as I can though.   Thanks!

Zappa

---

