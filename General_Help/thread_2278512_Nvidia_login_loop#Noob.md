---
title: "Nvidia login loop#Noob"
date: 2015-05-17
forum: General Help
---

### Post by paul208 on 2015-05-17
[SIZE=2]I'm a **new Ubuntu user** (Just installed it) I have dual booted Ubuntu 14.04 with Win 8.1 on my laptop and everything on Ubuntu seems fine,
 but the problem is that it is really slow and lags regularly, compared to Win8.1 Ubuntu runs like trash.
Because of that I decided to install **Nvidia drivers** (for GTX 860M 2gb), to try and solve the issue,
 but when ever I try to install them I get a** login loop**(Every time I try to login it takes me back to the login screen)
I can fix it by deleting the drivers, but it doesn't solve my primary issue.
Please help a** noob**:p[/SIZE]

---

### Post by efflandt on 2015-05-17
A gaming laptop should not lag in general web browsing and things, but may lag something awful if trying to play games using default Intel graphics.

You did not say how you installed/uninstalled nvidia drivers or which version. If it is the **nvidia-current** package that is tripping up on you, make sure that is completely removed and try **nvidia-331-updates** package. If you do not know how to do that, the easiest way would be to install **synaptic** from Ubuntu Software Center and synaptic can allow you to select more specific packages. Just make sure that you refresh synaptic first (curly arrow on it) then Quick search nvidia.

I don't think that Additional Drivers shows anything when you have hybrid Intel/Nvidia graphics, or at least it did not show anything on my laptop. I am using nvidia-331-updates for the GTX 765m on my laptop. But I am using a newer version nvidia-349 for desktop (from xorg-edgers ppa) which is a newer card that uses a new Maxwell chip that the 900 series use, despite its 700 series.

---

