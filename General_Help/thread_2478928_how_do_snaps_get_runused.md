---
title: "how do snaps get run/used?"
date: 2022-09-08
forum: General Help
---

### Post by Skaperen on 2022-09-08
the web pages i find online as i try to learn more about snaps are just stuffed with descriptions that seem more oriented to management people who are trying to make decisions.  this is fine for them but i just want (for now) simple and basic end user stuff.

Firefox is now a snap in 22.04.  so when someone uses 22.04 and they want to run Firefox, how is this done?  how is it different from the perspective of someone trying to avoid lots of technical details.

as for technical details, how do snaps share read-only memory for higher performance usage?

---

### Post by TheFu on 2022-09-09
Look at the menu.desktop files. The Exec= will show the exact command used.
blogs.ubuntu.com has lots of snap discussions going back to 2015. This is likely where the background you seek will be found.  Plus a basic knowledge of Linux cgroups and namespaces is needed.

---

### Post by grahammechanical on 2022-09-09
If you want to run/load a snap packaged application from the terminal just type the name of the application. On 22.04 the command

```
firefox
```

will load the Firefox web browser. The same applies to any installed snap packaged application.

Regards

---

### Post by Skaperen on 2022-09-10
so there is something like maybe a script that sets up things (like the mount to get to the executable, libraries it needs, etc) to be able to run the snap?  if i know something is a snap, i start with "which something" and go from there.

---

### Post by grahammechanical on 2022-09-11
This might help you

[https://snapcraft.io/docs/getting-started?_ga=2.5938867.1275793871.1552298901-273100804.1502190104](https://snapcraft.io/docs/getting-started?_ga=2.5938867.1275793871.1552298901-273100804.1502190104)

See the heading Run apps and commands from snap. It seems that the application is installed in /snap/bin/application-name. And that location should be part of the system's PATH. If not then this command should run a snap

```
/snap/bin/application-name
```

You will find folders for all installed snaps in /snap

Regards

---

### Post by Skaperen on 2022-09-12
yes, i have directory "/snap" and has one file "README" which has a little and a link which i have already looked at.  that directory has nothing else.  it looks like this snap stuff is intended to make portable apps even easier at the tradeoff of security. that's partly why i want to learn technical details.  i want to figure out what i need to do to run each snap in its own container.

---

