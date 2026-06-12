---
title: "Unable to Update Snap Store"
date: 2023-11-05
forum: General Help
---

### Post by tb75252 on 2023-11-05
I just upgraded to Ubuntu 23.10. 64-bit.
The system signals that Snap Store 41.3-71 is available.  But every time that I press the Update icon I get the following error message:
> Unable to update "Snap Store":
(null): cannot refresh "snap-store": snap "snap-store" has running
apps (ubuntu-software), pids: xxxx
...where xxxx changes every time that I run the update.
I tried killing the pid given but that does not seem to solve the problem...
Thanks for your help.

---

### Post by Rubi1200 on 2023-11-05
You could try this:

```
killall snap-store
```

---

### Post by tb75252 on 2023-11-05
> **Rubi1200 said:**
> You could try this:

```
killall snap-store
```
Unfortunately I am getting the same error message...

---

### Post by Rubi1200 on 2023-11-05
Make sure any Ubuntu Software apps are closed and try this:
```
sudo snap refresh snap-store
```

---

### Post by ian-weisser on 2023-11-05
> **tb75252 said:**
> 
...where xxxx changes every time that I run the update.
I tried killing the pid given but that does not seem to solve the problem...


This suggests that you are somehow (perhaps unintentionally) restarting snap-store after killing it.

Most commonly, this occurs when folks launch Ubuntu Software in order to reach the "Update" button.
The Ubuntu Software application is, of course, the same application as snap-store. It's the same application with two names. That's how it gets restarted.

You cannot use the Ubuntu Software "Update" button to update snap-store. Nobody can. It's the only snap that cannot use the "Update" button. Because it cannot update itself while it is running,
(yes, there's a bug report to remove the misleading "Update" button for that lone snap)

So what do you do?
Easy: You have two options.

Option 1: After killing the pid, run ```
sudo snap refresh
```

Option 2: After killing the pid, do nothing. In a few minutes or hours, the system will run the refresh automatically anyway.

---

### Post by tb75252 on 2023-11-05
> **Rubi1200 said:**
> Make sure any Ubuntu Software apps are closed and try this:
```
sudo snap refresh snap-store
```
This seems to have solved the problem.  But something strange has happened.  When I rebooted, the App Center icon had disappeared.  So I went in the Show Apps section, found the app and re-pinned it.  But when I launch the program things look different.  Where is the Update tab that was there before and was located at the top of the screen?

---

### Post by Dennis N on 2023-11-05
> **tb75252 said:**
> ...When I rebooted, the App Center icon had disappeared.  So I went in the Show Apps section, found the app and re-pinned it.  But when I launch the program things look different.  Where is the Update tab that was there before and was located at the top of the screen?

If you actually have the App Center, then you click on "manage" in the lower left corner to manage application updates. But, at this state of development, it seems to only handle snap packages, so it's not that useful.

App Center is not the same as Ubuntu Software. Depending on circumstances, you could have one or the other.

---

### Post by tb75252 on 2023-11-05
> **Dennis N said:**
> If you actually have the App Center, then you click on "manage" in the lower left corner to manage application updates. But, at this state of development, it seems to only handle snap packages, so it's not that useful.

App Center is not the same as Ubuntu Software. Depending on circumstances, you could have one or the other.
Thanks for the explanation.  I will mark this thread as solved.

---

### Post by jake4763 on 2024-02-19
To avoid the issue above and other related snap-store [bugs]("https://askubuntu.com/questions/1469200/how-can-i-dismiss-software-updates-installed-notification") and [failings]("https://forum.snapcraft.io/t/pending-update-of-snap-store-but-no-update-available/34415"), a couple of months ago I removed snap-store:
```
snap remove snap-store
```
This leaves the snap system intact, but just removes the troublesome snap-store.
Instead I now use gnome-software which manages snaps perfectly without any of the above issues. gnome-software also has the advantage that it handles flatpak and DEB packages.

---

