---
title: "Necessary to update?"
date: 2014-06-02
forum: General Help
---

### Post by 777funk on 2014-06-02
Seems like there are a lot of updates for 12.04 (seems daily on my machine). I have a slow connection and it's taxing to be always downloading things. Is it important to keep updating?

---

### Post by Impavidus on 2014-06-02
It's best to install at least the security updates. The other updates are less important. The update manager tells clearly which updates are security updates.

---

### Post by deadflowr on 2014-06-03
Do you have PPA's or something?
I don't get that many updates for 12.04.

That said, I also have my 12.04 system set up with both [unattended upgrades]("https://help.ubuntu.com/10.04/serverguide/automatic-updates.html") ([More]("https://help.ubuntu.com/community/AutomaticSecurityUpdates")) and [postfix]("https://help.ubuntu.com/community/Postfix") to mail me what updates came along.
If you setup unattended upgrades, its default settings is to only upgrade security fixes. 
But you can set it to install any other update-type, including updates from PPA's if you have them.

Even with this set up, I still don't get a ton of updates In fact, I can go several days without seeing any at all.

I still get notified weekly for all other updates.

Something else to chew on is if you have the proposed repo enabled, you might see quite a few more updates than someone who doesn't. Since those updates are sometimes unstable, they have a chance of getting pulled before making their way to the main repos.
If that makes sense.

---

