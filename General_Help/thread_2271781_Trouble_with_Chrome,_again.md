---
title: "Trouble with Chrome, again"
date: 2015-04-01
forum: General Help
---

### Post by Lloydb39 on 2015-04-01
I had Chrome working once. It got balky so I switched to Firefox. Wanted to do something with Chrome again and it wouldn't start, so I reinstalled the AMD 64-bit version on my AMD 64-bit computer. tried to start with google-chrome-stable from the terminal and got this:
[7156:7156:0401/113001:ERROR:process_singleton_posix.cc(277)] Failed to create /home/lloyd/.config/google-chrome/SingletonLock: File exists
[7156:7156:0401/113001:ERROR:chrome_browser_main.cc(1209)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

Anybody know what's up with that?

---

### Post by slickymaster on 2015-04-01
Try renaming or deleting the **SingletonLock** file and run google-chrome again. It will create the file again and will run normally.

---

### Post by Lloydb39 on 2015-04-01
I took the extra step of uninstalling, deleted all the Singletonlock files and then installed again. Seems to work now.

---

