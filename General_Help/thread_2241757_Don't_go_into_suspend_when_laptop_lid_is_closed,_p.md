---
title: "Don't go into suspend when laptop lid is closed, power manager problem"
date: 2014-08-28
forum: General Help
---

### Post by iums1 on 2014-08-28
When i close my laptop lid the system goes into suspend mode despite my power manager settings. Why is that?
 I never want the system to go into sleep, hibernation or suspend. I want the screen to turn off after 10 minutes of inactivity, that's all i want. 


[IMG]http://i60.tinypic.com/24fg2lx.jpg[/IMG][IMG]http://i62.tinypic.com/jr4a9z.jpg[/IMG]

---

### Post by The Cog on 2014-08-28
See this link: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1307545](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1307545)

especially this paragraph:
> The workaround mentioned in the bug description of #1222021 works.
( "WORKAROUND: This can be adjusted in /etc/systemd/logind.conf. Just set HandleLidSwitch and other the events you want handled by systemd to "ignore" - you have to delete # in the beginning of the respective lines -, save, close the file, and restart." )

So put this line in /etc/systemd/logind.conf:
```
HandleLidSwitch=ignore
```

---

