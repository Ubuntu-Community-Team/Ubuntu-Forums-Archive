---
title: "[lubuntu] - Customizing Guest not working"
date: 2017-02-16
forum: General Help
---

### Post by guysmiley on 2017-02-16
I have followed the official documentation for customizing the guest session from here: [https://help.ubuntu.com/community/CustomizeGuestSession#Special_purpose_user]("https://help.ubuntu.com/community/CustomizeGuestSession#Special_purpose_user").
In my case, I customized Firefox to have a particular homepage and autostart on login.  Neither of these events are occurring despite the fact I created /etc/guest-session and made a symbolic link using sudo ln -s /home/guest-prefs /etc/guest-session/skel

Help please :)

---

### Post by guysmiley on 2017-02-17
I also see an error on boot in Guest Mode that is well documented in Lubuntu circles (Guest Session cannot start Error PID#).  I wonder if because the session is not starting correctly that the traditional instructions for customizing the Guest Session (as linked to above) do not function.

---

