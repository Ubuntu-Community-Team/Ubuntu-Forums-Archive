---
title: "Guest as autologin user in Lubuntu 20.04"
date: 2020-10-01
forum: General Help
---

### Post by az64x on 2020-10-01
How do I set the id Guest as the default user and automatic login (no password)

---

### Post by CelticWarrior on 2020-10-01
You don't.

Guest isn't available anymore and should never have been.
The same goes for autologin. Although you can enable it for your user, you definitely shouldn't.
Please follow good practices for your own safety.

---

### Post by Impavidus on 2020-10-02
I never used a guest session myself, but have a look at these links:
[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)
[https://askubuntu.com/questions/1112349/how-to-enable-guest-sessions-on-ubuntu-18-04-or-later](https://askubuntu.com/questions/1112349/how-to-enable-guest-sessions-on-ubuntu-18-04-or-later)

It seems there are some problems with that. But I also see that for some people it's either a guest session (or something like it) or no computer at all. OP posted this thread earlier:
[https://ubuntuforums.org/showthread.php?t=2451053](https://ubuntuforums.org/showthread.php?t=2451053)

---

### Post by az64x on 2020-10-02
This is for computers in a computer lab.

So guest seemed like a good idea.

---

### Post by guiverc on 2020-10-02
`sddm` (used by Lubuntu) does not have any provision for a 'guest' login.

Refer [https://github.com/sddm/sddm/issues/1091](https://github.com/sddm/sddm/issues/1091)

*There is more detail somewhere, but I don't have time to search for it, and it wasn't easy fixes, or for some reason I wasn't happy with it so didn't remember it, but could just have been I've no use-case for guest sessions thus saw little need to remember it.*

---

