---
title: "Auto-Login Xubuntu Minimal 15.04"
date: 2015-05-03
forum: General Help
---

### Post by evan8 on 2015-05-03
Okay. So, I installed Xubuntu-minimal from ubuntu mini 15.04

I notice the User-Groups is not in the Settings. Normally I would just edit the lightdm.conf but I also cannot find it. It's not in /etc/lightdm/ and in other spots I have checked.

So, anybody know the specific package to get the GUI user-accounts going on for settings? Or know how to manually set it for auto?
thanks in advance. Just moved form arch and I guess some things are different.

---

### Post by kerry_s on 2015-05-03
sudo apt-get install gnome-system-tools

---

### Post by evan8 on 2015-05-03
hehe I almost did that earlier but it just felt wrong. Okay Will give it a go. thanks

well that got the user groups in my settings. But I still have to press Enter. Where does ubuntu hide the lightdm.conf at?

---

### Post by evan8 on 2015-05-03
Oh well. I got my lightdm greeter looking all cute now. May as well  just figure it out later. Odd how it's different on here than Arch a bit.

---

### Post by kerry_s on 2015-05-04
> **evan8 said:**
> Oh well. I got my lightdm greeter looking all cute now. May as well  just figure it out later. Odd how it's different on here than Arch a bit.

that's because in arch you have to configure manually. get's tiring after awhile, sure you can get a faster system, but you have to work at it, to much up keep. lol
i ditched arch ages ago.

why didn't you just do the full xubuntu install ? it's much easier to remove things than figure out whats missing.

i'm using a hp mini 210-1010nr netbook, tiny 10" screen & low specs. lol

---

### Post by evan8 on 2015-05-04
Yeah. I just moved from Arch. I had a system break and I told myself it that ever happened with Arch I'd leave it. So, I did. Been enjoying ubuntu. Just getting used to it again. My systemd-analyze boot time is much slower though. Not sure why. Could be daemon related .But I feel more comfty here.

Also using 4.1 kernel without issues.

Got off topic:p

---

