---
title: "Polkit issue with Ubuntu 24"
date: 2024-08-01
forum: General Help
---

### Post by kladizkov on 2024-08-01
I have an issue with Polkit after migrating to Ubuntu 24 from Ubuntu 22.

In ubuntu to disable the Shutdown, Suspend option for users, I create /etc/polkit-1/localauthority.conf.d/10-onlyrestart.pkla file with the below content.

```
[OnlyRestart]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.stop;org.freedesktop.login1.power-off;org.freedesktop.login1.power-off-multiple-sessions;org.xfce.session.xfsm-shutdown-helper;org.freedesktop.login1.suspend;org.freedesktop.login1.suspend-multiple-sessions;org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.consolekit.system.stop-multiple-users
ResultInactive=no
ResultActive=no
```

This doesn't work now in Ubuntu 24. How to make it work in Ubuntu 24?

Please help!

---

### Post by currentshaft on 2024-08-01
sce

---

### Post by kladizkov on 2024-08-02
> What does "doesn't work" mean?

I'm trying to prevent non-root users from shutting down the workstation from XFCE logout menu. Here except for 'Logout' all other buttons viz Shutdown, Restart etc need to be disabled. These buttons are still enabled even after adding the configuration in /etc/polkit-1/localauthority.conf.d/10-onlyrestart.pkla. That way it doesn't work. This was working in Ubuntu 22 but not in Ubuntu 24.

>  Have you restarted polkit after applying the changes?

Yes, I have tried restarting.

>  Does the user which this does not apply to have root privileges?

This does not apply to any user at all.

>  Also, double-check the actions you're setting with "pkaction --verbose"                 

The change is not reflected in "pkaction --verbose". The result doesn't show the things I added.

---

### Post by kladizkov on 2024-08-02
Finally made it working. Polkit has got many changes and JS is needed. After adding the below lines to /etc/polkit-1/rules.d/50-disable-shutdown.rules

```

polkit.addRule(function(action, subject) {
    if ((action.id == "org.freedesktop.consolekit.system.stop" ||
         action.id == "org.freedesktop.login1.power-off" ||
         action.id == "org.freedesktop.login1.power-off-multiple-sessions" ||
         action.id == "org.xfce.session.xfsm-shutdown-helper" ||
         action.id == "org.freedesktop.login1.suspend" ||
         action.id == "org.freedesktop.login1.suspend-multiple-sessions" ||
         action.id == "org.freedesktop.login1.hibernate" ||
         action.id == "org.freedesktop.login1.hibernate-multiple-sessions" ||
         action.id == "org.freedesktop.consolekit.system.stop-multiple-users")) {
            return polkit.Result.NO;
    }
});

```

It is working now.

---

