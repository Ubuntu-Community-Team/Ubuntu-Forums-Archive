---
title: "Configuring osd notifications"
date: 2014-07-10
forum: General Help
---

### Post by startas on 2014-07-10
How to configure osd notifications ? I havent found any tool yet, and that kind of old ppa doesnt really work that good. I would like to reduce on screen time to 1 second and disable notifications from custom programs, like browsers, players, downloaders and so on, leaving just system notifications, like volume up/down, screen brightness and so on.

---

### Post by ian-weisser on 2014-07-10
You, the user, have no control over which notifications get delivered to you, what they look like, or how long they last. You also have no way to "block" notifications that you don't value.

Those, and more, _are_ customizable...but only by the originating application. If you feel that a notification is unclear, poorly worded, undesirable, annoying, missing, or has the wrong timeout value, please file a bug against the application so the developers can reproduce the issue and fix it, or provide customization settings within the application.

The notification system (library) is simply queueing and a delivery system. It has no way to gauge the content or value of a notification, nor any way to evaluate or override the values that an application has assigned.

---

