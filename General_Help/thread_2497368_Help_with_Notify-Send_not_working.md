---
title: "Help with Notify-Send not working"
date: 2024-05-02
forum: General Help
---

### Post by goemonburo on 2024-05-02
I have been trying to get a simple alert show up when I complete a bash script, and it works fine as a regular user.  But I have to run the program as sudo, and for some reason, when I do, notify-send fails.  Does anyone know why?  Is there a way to fix this?  Can I tell notify-send to appear on a certain user's active desktop?

The line in the script is:

notify-send -u critical -t 0 "Some text here."

Any help will be appreciated.  Thank you!

---

### Post by ActionParsnip on 2024-05-02
Try adding an export to set the DISPLAY value. May help

---

### Post by Holger_Gehrke on 2024-05-03
notify-send uses the session-dbus to send the notification to a notification daemon. It needs the environment variable DBUS_SESSION_BUS_ADDRESS to have the correct value ('unix:path=/run/user/1000/bus' on my system; '1000' is my numeric user id) and it must be called by the user (the dbus protocol has some authentication mechanism in place). So what you should try in your script is something like
```

su -c "DBUS_SESSION_BUS_ADDRESS='unix:path=/run/user/UID/bus' notify-send 'blah'" - USER

```
Replace UID and USER to fit your situation.

Holger

---

### Post by goemonburo on 2024-05-03
@Holger_Gehrke, that worked perfectly.  Thank you so much!

---

