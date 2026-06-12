---
title: "flash issues (continued)"
date: 2007-12-19
forum: General Help
---

### Post by sethfc on 2007-12-19
OK, this is somewhat a continuation of my last thread, where i was trying to manually install flash.

I reformatted my ubuntu, performed all updates.

I went to youtube.com, tried to view a video.  Firefox prompted me to install a plugin.

The two plugin options were: gnash (nasty), and adobe flash.

I selected to install adobe flash.  Install completed, firefox reloaded the page, but it still said I needed to install a plugin.

I restarted my computer, same thing occurs.

ANY suggestions?

thanks,
seth

---

### Post by tshrinivasan on 2007-12-19
try
1. remove flash-plugin
2. remove firefox
3. install firefox
4. install flash-plugin

---

### Post by Sef on 2007-12-19
> OK, this is somewhat a continuation of my last thread, where i was trying to manually install flash.

1) Uninstall flash.  (Check on how to install a tar.gz file.  I will post it if i can find something on how to do it.)

2) Reinstall flash via Applications > Add/Remove > set top right box to all "available applications" > search > Adobe > select the top option (Macromedia Flash Plugin) > Apply > Apply > close

---

### Post by Zack McCool on 2007-12-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The Flash plugin in the Gutsy repositories is currently problematic.  Adobe changed the version of Flash on their site, and the repository has the MD5Sum for the old version.  The installer does not include the plugin, but rather downloads it from Adobe's site during the install (License restrictions).

There are solutions, but they are not necessarily straightforward.  See this thread, and read it carefully for the fix, and all of the possible ramifications:

[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

