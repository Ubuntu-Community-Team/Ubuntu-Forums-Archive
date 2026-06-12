---
title: "updating-upgrading questions"
date: 2006-11-14
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-14
This is the situation: Ihave burned many ISO's of Edgy and they do not boot on my system. So here is my option and question. I have a Dapper cd from ship-it. When I install Dapper, it wants to do about 900 updates right after install is done. Do I let it do updates BEFORE I start upgrade or right after install can I do gksudo update-manager -c ? Or should I do: sudo aptitude update && sudo aptitude dist-upgrade right after Dapper install. I guess my point being is I do not want to install Dapper then sit through 900 Dapper updates then upgrade to Edgy then sit through another 900 Edgy updates. Maybe I am confused by all this. None the less I have to start with a Dapper cd regardless as that is what I have to work with. Also should be noted that I am going through this as I am not getting replies to earlier thread "Where did my Repositories go". Thank you to any one who can guide me :)

---

### Post by nikhilk on 2006-11-14
> **MustangSallydd said:**
> 
I guess my point being is I do not want to install Dapper then sit through 900 Dapper updates then upgrade to Edgy then sit through another 900 Edgy updates.

Yes, I guess that is the sensible thing to do. You would be better off doing a "gksudo update-manager -c" immediately after the Dapper install without waiting for the Dapper upgrades.
Do correct me if I am wrong, since I haven't tried it myself.

---

### Post by pliumbum on 2007-02-07
excuse me for what may seem a stupid question, but I am a bit of a newb. I hear that Feisty is coming off in april, so sure I will want to use the newer version of Ubuntu. Will I be able to upgrade from Edgy without deleting my hard drive? I mean I dont want to have two OS on the comp, just want to upgrade.

---

