---
title: "Newbie using Ubuntu 21.04, Problem with ‘Metered Connection’."
date: 2021-08-29
forum: General Help
---

### Post by Advait on 2021-08-29
[COLOR=#1d1c1d][FONT=Arial]See image. Updates paused but metered connection box unchecked. How to fix this? [/FONT][/COLOR]
[COLOR=#1d1c1d][FONT=Arial]The solution should be something a newbie can implement.[/FONT][/COLOR]
[COLOR=#1d1c1d][FONT=Arial]This thread is relevant [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial][/FONT][/COLOR]]("https://gitlab.gnome.org/GNOME/gnome-software/-/issues/996")[COLOR=#1155cc]_[https://gitlab.gnome.org/GNOME/gnome-software/-/issues/996](https://gitlab.gnome.org/GNOME/gnome-software/-/issues/996)_[/COLOR][COLOR=#1d1c1d][FONT=Arial] but I was unable to follow all the posts that had lots of terminal commands. Is that the only way to fix this?[/FONT][/COLOR]
[COLOR=#1d1c1d][FONT=Arial]( I found this link in this thread [https://ubuntuforums.org/showthread.php?t=2449764](https://ubuntuforums.org/showthread.php?t=2449764) )

Can I get around this issue by just manually running 'sudo apt update' and 'sudo apt upgrade'? Will that upgrade the same group of apps?


.
.

[/FONT][/COLOR]

---

### Post by ajgreeny on 2021-08-29
You or more accurately, the system, are trying to run updates on a metered connection. I don't use auto updates nor a metered connection but I think you need to turn off autoupdates and use the update manager or those apt commands you mention; the same packages will be updated.

This is one of the several reasons why some users, including me, turn of auto updates completely but it does mean that you have to ensure that you manually update frequently which is an important maintenance action.

---

### Post by Advait on 2021-08-29
> **ajgreeny said:**
> You or more accurately, the system, are trying to run updates on a metered connection.

But the 'metered connection' box is unchecked. So why does it think the connection is metered? Is there some setting on my Android Samsung smartphone that is telling Ubuntu that the connection is metered?

----------------
> **ajgreeny said:**
> but I think you need to turn off autoupdates and use  the update manager or those apt commands you mention; the same packages  will be updated.

OK. I can do that. But I'd still like to fix the underlying problem. Can it be fixed? Or is this a known, unfixed Gnome/Ubuntu/Linux bug?

---

### Post by Advait on 2021-08-29
Problem solved with command: nmcli connection modify Galaxy\ A71BD53 connection.metered no

---

