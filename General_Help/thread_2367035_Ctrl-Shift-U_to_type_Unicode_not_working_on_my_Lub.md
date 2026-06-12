---
title: "Ctrl-Shift-U to type Unicode not working on my Lubuntu 16.04"
date: 2017-07-25
forum: General Help
---

### Post by schamane2 on 2017-07-25
[Edit 2017-07-25 14:51: Only later I found that it does work as  advertised on 2 other Lubuntu installations. I am now trying to find why  it doesn't work on one particular installation.]

All guides I found about how to type any unicode characters by means of their, e.g. <U+1F60A>, say that it should work with Ctrl-Shift-U. I have no Ubuntu with Unity at hand but I guess that it would work.

But it does not work on my Lubuntu 16.04 with Openbox. How do I enter unicode characters (without copy/paste)?

---

### Post by shantiq on 2017-07-25
Do you release Ctrl-Shift after Ctrl-Shift-U ? to type 1F60A or do you keep them pressed in ....  I found sometimes it works one way or the other or both ...   maybe you have tried this already?

---

### Post by schamane2 on 2017-07-25
> **shantiq said:**
> Do you release Ctrl-Shift after Ctrl-Shift-U ? to type 1F60A or do you keep them pressed in ....  I found sometimes it works one way or the other or both ...   maybe you have tried this already?

Thanks, I didn't know that both ways can work. Still, indeed, I tried it both ways. But more importantly: I now had a chance to try it on my office Lubuntu and on a freshly booted Live-CD with Lubuntu 16.04.2. It works in both cases as advertised!

So, I need to figure out why it doesn't work on my home PC which runs the same system. Any idea where I should start looking?

---

### Post by schamane2 on 2017-07-27
So far I found that Ctrl-Shift-U worked when I logged in as guest. Then I rebooted and now it works also in my main account. Still no clue why it failed at first.

---

### Post by shantiq on 2017-07-27
go figure! damn machines :] happens to us all time and time again ....

---

### Post by schamane2 on 2017-08-03
Still no problems after a few more updates, changes, reboots and hibernation cycles. I think we can safely assume that one the system updates broke the unicode ^Sh-U entry. According to the logs there were systemd and udev updates applied that certainly cautioned a reboot which was still due when I happened to try ^Sh-U again.

Probably, it would have been sufficient to just logout and login. Still, system updates should be followed by reboots anyway.

---

### Post by shantiq on 2017-08-03
[SIZE=5]&#128077;[/SIZE]  :]     u+1f44d

---

