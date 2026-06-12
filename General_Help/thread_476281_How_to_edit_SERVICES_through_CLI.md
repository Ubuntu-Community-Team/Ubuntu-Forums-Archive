---
title: "How to edit SERVICES through CLI"
date: 2007-06-17
forum: General Help
---

### Post by database_dan on 2007-06-17
I went to System > Administration > Services and turned off a few things that I don't need. Since I don't have any BlueTooth devices or printers, I figured I would free up some CPU cycles by turning these off. I must have turned something else important off, because now when I log into X I get the "Failed to initialize HAL!" error. So far everything seems to work...

When I go back into System > Administration > Services, I get the error "The configuration could not be loaded. You are not allowed to access the configuration."

So can someone tell me where the file is that contains the settings for the services (for Feisty Fawn)?

Thanks,
~Dan

---

### Post by database_dan on 2007-06-17
i figured it out for those who are interested (each service has its own start up script in this directory).

```
sudo /etc/init.d/dbus start
```

this did several things, one of which included turning Hardware Abstraction Layer (HAL)

once that was started, i was able to to go into system > administration > services and turn DBUS on by default so that it runs when Ubuntu is started.

---

