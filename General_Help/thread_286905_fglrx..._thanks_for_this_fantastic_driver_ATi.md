---
title: "fglrx... thanks for this fantastic driver ATi"
date: 2006-10-28
forum: General Help
---

### Post by Amt0571 on 2006-10-28
The title of the post is sarcastic, of course. I'll explain my problem:

I have a Radeon 8500LE which worked well (with some very ocassional freezes) on Dapper. However, in edgy things have got worse.

After spending two hours trying to get rid of the mesa issue, I figured it out that fglrx and agpgart were not added to /etc/modules. After manually adding them, the messa issue went away.

However, now the computer freezes after a few minutes or sometimes even when it loads the gnome-panel (even if I'm not running any 3D app). The curious thing is that 3D apps work well (until they also freeze, of course).

If I disable fglrx, the crashes go away, but of course, I lose 3D acceleration.

I have also tried to use the open source driver, but for some reason it crashes after a few seconds in any 3D app (it happened in Dapper also).

I don't think it's a hardware problem, since the same system works without problems in Windows XP.

I'm thinking about testing if this card can fly by throuwing it out of the window, and buying a nVidia one... but I hope someone here will have a better solution :)


Thanks!

---

### Post by bionnaki on 2006-10-28
maybe this will help 
[http://www.ubuntuforums.org/showthread.php?p=1669992#post1669992](http://www.ubuntuforums.org/showthread.php?p=1669992#post1669992)

---

### Post by Amt0571 on 2006-10-28
I have already disabled composite, so I don't think this is the problem.

Thanks anyway

---

### Post by twistedwrench on 2006-10-28
Having the same problem with radeon 9800 pro](*,) . Actually checking account balance for the funds for an NVidia then it's Flying lessons for the ATI!;)

---

### Post by graigsmith on 2006-10-28
try selling the card online. and then use the money to buy nvidia.

---

### Post by Amt0571 on 2006-10-28
Well... the problem is that nVidia cards give me BSODs in that computer (at least a 6600GT did)... and my experience with nVidia+Windows is quite bad... I'm not sure what to do...

Anyway, I did a fresh install of Kubuntu this afternoon and it seems the open source driver crashes are no longer present. Also, somehow Ubuntu seems a lot faster now... but maybe this is because I'm using now KDE instead of Gnome... I'm not sure. I think I'll continue this way if I can...

Thanks!

---

### Post by tedrogers on 2006-10-28
[http://ubuntuforums.org/showthread.php?t=93715](http://ubuntuforums.org/showthread.php?t=93715)

Try this....this little addition to my boot files changed everything for me.

---

### Post by Amt0571 on 2006-10-28
No luck... and now the ati opensource driver started to crash... I think it's time for flying lessons...

---

