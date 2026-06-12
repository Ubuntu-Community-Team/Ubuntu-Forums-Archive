---
title: "FFmpeg not installed but Lubuntu wants to install security updates"
date: 2016-12-16
forum: General Help
---

### Post by saintsfan342000 on 2016-12-16
Sorry if the title was confusing.  Attached a screenshot of my Software Updater, which is telling me it wants to install some security updates for FFmpeg.  I ran "locate ffmpeg" and sure enough there are some files in /var/lib/dpkg, but the program isn't installed.  

Anyone know then what these updates mean or what their purpose is?

---

### Post by DuckHook on 2016-12-16
The **app**, *ffmpeg*, is not installed in your OS, but the **libraries** are, and this is as it should be. You need the library files to be able to play back various media. The app, on the other hand, is a metapackage with CLI tools used to convert formats, play media (via command line), manipulate media files, etc. You probably don't want the app bundle unless you are a command line jockey who eschews GUIs.

You should allow the updates to proceed. They are security updates, which are all the more necessary to apply.

---

