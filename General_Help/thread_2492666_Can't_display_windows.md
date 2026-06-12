---
title: "Can't display windows"
date: 2023-11-19
forum: General Help
---

### Post by tom46512 on 2023-11-19
On Ubuntu 23.10 I can't see file open window in Visual Studio Code, the window is malformed also the same issue I have with JOSM (java base editor for OpenStreetMap). I have Ubuntu on Virtualbox 7.0.12. this issue has started after upgrade to 23.10, I have installed Guest Virtualbox Additions.

---

### Post by MAFoElffen on 2023-11-19
<<This should be moved to the "Virtualization" Section, where it will get exposure to VBox users >>

Could you please be more specific and descriptive? I'm having a problem understanding what you described. Let me try to reword that, and tell me if I am describing that or not... 

In your VBox VM Ubuntu Guest, that you have Visual Studio Code & JOSM installed, but those have rendering problems when those applications start.

Could you please attach screenshots of that to a post so we can see what is happening?

Also, please post the results of
```

printenv XDG_SESSION_DESKTOP

```

---

### Post by tom46512 on 2023-11-19
Right, 

In most cases everything works as expected, I can run chrome and browse
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=293082&stc=1[/IMG],
but when I go to VSC it also shows correctyl but when I try to open files the new window is doesn't show correctly 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293085&stc=1[/IMG]

also I have issue to use JOSM, 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293083&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293084&stc=1[/IMG]

output of cmd 
```
xxx@xxx:~$ printenv XDG_SESSION_DESKTOP
ubuntu

```

When I try to open file or see about in VSC in syslog I'm getting msg
```
2023-11-21T02:45:37.807315+01:00 xxx gnome-shell[2862]: Meta.Rectangle is deprecated, use Mtk.Rectangle instead
2023-11-21T02:45:43.734636+01:00 xxx gnome-shell[2862]: message repeated 38 times: [ Meta.Rectangle is deprecated, use Mtk.Rectangle instead]
```

---

### Post by MAFoElffen on 2023-11-21
In the VBox VM config, turn off Hardware Acceleration. In VS Code, turn off the hardware acceleration setting in it's settings.

Did that help with that?

---

### Post by tom46512 on 2023-11-22
Yes, now it works!  I have turned off hardware acceleration in VM Config, extended mem for graphic card  to max and disabled hardware acceleration in VS Code, thx a lot !

---

