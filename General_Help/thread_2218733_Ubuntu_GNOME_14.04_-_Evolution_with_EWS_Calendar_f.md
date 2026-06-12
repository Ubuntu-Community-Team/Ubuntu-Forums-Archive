---
title: "Ubuntu GNOME 14.04 - Evolution with EWS: Calendar freezes"
date: 2014-04-21
forum: General Help
---

### Post by crooked_smile on 2014-04-21
Hello all,

I upgraded my work laptop to Ubuntu GNOME 14.04 last week with relatively few issues. However, I ran into what appears to be a nasty bug with running the Evolution email client 3.10.4 with the Exchange Web Services (EWS) plugin. After configuring my work Exchange account, email, contacts, and calendar reminders appear to be working with no problems. Yet, when I click on the Calendar button to view my calendar, Evolution completely locks up. I manually killed all Evolution-related processes using the system monitor, but re-launching Evolution takes me back directly to the Calendar, freezing the email client once again. If I wait long enough (about 15 - 20min) the email client seems to return back to normal, but will freeze again if I click Calendar once more. I was able to recreate the issue on a VM as well when trying to view the calendar by month.

I did a little research before posting and found someone had the exact same problem with Evolution running on Fedora. The original link can be found here:

[https://bugzilla.redhat.com/show_bug.cgi?id=1075461](https://bugzilla.redhat.com/show_bug.cgi?id=1075461)

The issue appears to be with the evolution-data-server component, and a patched version of the component evolution-data-server-3.10.4-3 was released to resolve the issue. I tried looking online for an Ubuntu compatible version of the patch but have fallen short. 

Does anyone know of a way I can patch this component or of another solution to this issue? Unfortunately I can't switch to another email client, as Evolution seems to be the only Linux client that supports MS Exchange Web Services decently, and the Exchange 2007 OWA site is barely usable unless you're running IE6+. Our system admins don't seem to be in a hurry to upgrade the Exchange environment anytime soon, so I'm pretty much stuck with what I got.

Thank you,

---

### Post by z-christian on 2014-04-30
Hi,  I am also very interested in a fix for Ubuntu here... anyone that have any kind of information on this:

[https://git.gnome.org/browse/evolution-data-server/commit/?id=6b9b325](https://git.gnome.org/browse/evolution-data-server/commit/?id=6b9b325)

---

