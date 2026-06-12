---
title: "Ubuntu 22.04 Screenshot Problem"
date: 2023-01-25
forum: General Help
---

### Post by stefankochinsky on 2023-01-25
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit]Hello. I have a problem with ubuntu 22.04 LTS with the screenshot tool (Upwork) This app takes a screenshot every 10 minutes while it's running. And now every 10 minutes I get a request for permission to take a screenshot. As far as I understand this security problem lies in the restrictions from Weyland and gnome 42. (X org works fine)[/FONT][/FONT][/FONT][/FONT][/COLOR][FONT=-apple-system][FONT=inherit]
[/FONT][/FONT][COLOR=#232629][FONT=-apple-system][FONT=var(--theme-post-body-font-family)][FONT=inherit]How can this problem be solved?[/FONT]
[FONT=inherit]PS. I know that the problem is already solved in gnome 43, and there the resolution appears only once. But I think that ubuntu 22.10 is not stable and not suitable for daily work.[/FONT]
[FONT=inherit]I will be glad for any help. Many thanks[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-01-25
Could use gnome-screenshot
```

/usr/bin/gnome-screenshot -a -f /home/foo/Pictures/screenshot-$(date +"%Y_%m_%d_%I_%M_%p")

```
Obviously change "foo" to your actual username. You can then cron this command to run as you require.

HTH

---

### Post by stefankochinsky on 2023-01-26
Thank you for your reply. 
Looks like it can't be fixed at any way, so I can use it only with Gnome 43
And with 42 it can be request every time
Thank you

---

