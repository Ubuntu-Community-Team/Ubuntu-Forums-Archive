---
title: "[SOLVED] 6200 and ubuntu problem with compiz please help!  :("
date: 2008-06-18
forum: General Help
---

### Post by pantelis_21 on 2008-06-18
i have just bought a nvidia 6200 to be able to run compiz, but the big problem is that after some time running compiz some strange stripes appear on  my desktop, i thing that they appear more at the place i move my mouse and there is text there, i tried ubuntu 7.10, then installed kubuntu 8.04 but the problem is still here, please if anyone can help me, it is very strange problem because compiz runs well for a little time but after a while the problem appears, i attach two snapshots of the problem, if i stop compiz running, the stripes sometimes disappear and some other times are still there...

---

### Post by Exsecrabilus on 2008-06-18
Do you update using *hardy-proposed* or *hardy-backports*?

---

### Post by pantelis_21 on 2008-06-18
no, i have enabled only important security and recommended updates, have you excperienced a problem like this? it is very strange, isnt it? it runs excellent for 5 minutes and after that the problem!

---

### Post by Happy_Man on 2008-06-18
It might just be a conflict between the KDE environment and Compiz.

---

### Post by pantelis_21 on 2008-06-18
i dont know if it is a conflict,


[http://www.youtube.com/watch?v=NkCu_FXoD3g](http://www.youtube.com/watch?v=NkCu_FXoD3g)


somedy just run it with a geforce 6200 and it seems that there are no problems, i am afraid if something isnt configured properly... could it be a wrong configured xorg.conf? or no? i dont know many things about video cards and ubuntu/kubuntu.... but i hate this problem, why to have it perfect for a while and after 5 minutes broken? if there is a bug or something like that i would prefer it to cause the problem from the beginning! it makes me to love it and then it kills me... :) so, i believe that maybe a configuration should solve this problem, has anybody a good idea for this?

---

### Post by Exsecrabilus on 2008-06-19
> **Happy_Man said:**
> It might just be a conflict between the KDE environment and Compiz.
He tried this with GNOME too.

---

### Post by pantelis_21 on 2008-06-19
some bad news! i have runned 2 or 3 times "glxgears"  without problem, but today the problem i described above appeared when i runned glxgears, fps were very good but after a little time as you can see to the screenshots... *boom!!!* could it be a driver bug? at these screenshots i DID NOT run compiz, so i can now say that this  problem appears when i run compiz and a little time passes (when i see video this time is smaller) and sometimes when i run "glxgears"... any opinion? 



it is a little stupid, now i run glxgears without problem, so the problem appears sometimes...

---

### Post by pantelis_21 on 2008-06-20
i solved that, i installed xgl and everything now works fine, how can i close this thread????


ok, i found that...

---

