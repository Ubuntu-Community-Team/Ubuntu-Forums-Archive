---
title: "Gnome Failed to synchronize extensions: CantInstallError"
date: 2020-09-22
forum: General Help
---

### Post by Paddy Landau on 2020-09-22
Several times during the day, I receive a notification with this error:

GNOME Shell integration
Failed to synchronize extensions: GDBus.Error:org.gnome.Shell.CantInstallError: This is an extension enabled by your current mode, you can't install manually any update in that session.

I think that I know what it's about. The Gnome extension "Desktop Icons", which comes installed by default, was giving repeated errors that I couldn't fix. Following instructions, I uninstalled it manually (it won't uninstall through the [Gnome Extensions]("https://extensions.gnome.org/local/")), and replaced it with [Desktop Icons NG (DING)]("https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/"), which has far superior functionality, and doesn't give problems.

I believe that Gnome is repeatedly trying to reinstall the old Desktop Icons, and failing. I could be wrong!

Do you think that I'm right about this error?
If so, how can I disable this error?
If not, how can I find out what this error is about?

**EDIT**

[FONT=Verdana]This is definitely related to desktop-icons@csoriano, as I find that I have a related error every time at the same time.[/FONT]

[FONT=Verdana]As I've had no response to this thread, I've opened a [/FONT][new thread with further details]("https://ubuntuforums.org/showthread.php?t=2451424") to replace this thread[FONT=Verdana].[/FONT]

---

