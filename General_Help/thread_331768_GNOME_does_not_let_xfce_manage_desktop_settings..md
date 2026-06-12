---
title: "GNOME does not let xfce manage desktop settings."
date: 2007-01-05
forum: General Help
---

### Post by muxecoid on 2007-01-05
I've installed xubuntu-desktop under ubuntu and started using XFCE. Sadly enough GNOME often takes over the desktop and I need to re-set xfce as desktop manager in XFCE settings. It happens regardless of the state of "Save session" check-box. How do I set XFCE as unoverwritable desktop manager? (at least during xfce sessions)

---

### Post by Joeb on 2007-01-06
Are you running nautilus under XFCE?  If so, it takes over the desktop unless you launch it as nautilus --no-desktop   

Of course, once it has taken over the desktop and you have saved the session, you're stuck.  I think you can open a terminal and issue a command such as   killall nautilus  to get rid of it, then exit XFCE and save your settings.

---

### Post by Dwood108 on 2007-10-20
you can also try this:

   1. In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."
   2. Log out and log back in.
   3. Click 'New Session' when the session selector appears, and name it whatever you want.
   4. The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.

once this works you can turn off the session selector at startup and go directly to your new session on future logins.

---

