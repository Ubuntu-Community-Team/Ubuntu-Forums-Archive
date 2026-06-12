---
title: "&quot;Firefox Already Running&quot;"
date: 2014-03-28
forum: General Help
---

### Post by robin7 on 2014-03-28
It happens fairly often, but not predictably.  I'm in and out of Firefox throughout the day, and once in a while I get this when I go to open it:

> Firefox is already running but is not responding.  You must either close Firefox or restart your system.

I check, and Firefox isn't running at all.  I enter "top" in a terminal and Firefox does not appear in the list of running software.

Only a reboot restores access to Firefox!  It happens almost daily.  Is there some setting that needs to be changed?

I'm running Xubuntu 12.04 

Thanks!
[ATTACH=CONFIG]251531[/ATTACH]

---

### Post by slickymaster on 2014-03-28
["Firefox is already running but is not responding" error message - How to fix it]("https://support.mozilla.org/en-US/kb/firefox-already-running-not-responding#w_remove-the-profile-lock-file")

---

### Post by mikewhatever on 2014-03-28
You can kill the firefox proccess with **pkill firefox**. Top shows all running processes (usually over 100), and firefox may be off the screen. Run **ps ax | grep firefox** to check.

---

### Post by SeijiSensei on 2014-03-28
As the link from slickymaster points out, you need to remove the .parentlock file from your Firefox profile.  

The profile is stored as $HOME/.mozilla/abcdefgh.default, with "abcdefgh" replaced by a random string of letters and numbers.  Inside the profile folder you'll find a file called .parentlock.  With Firefox completely shut down, delete that file.  Firefox will start normally again.

The .mozilla directory and the .parentlock file are examples of "hidden" files.  Files beginning with a dot are not normally displayed unless you enable the "Show Hidden Files" option in programs like Nautilus or Dolphin.  If you're comfortable with the command prompt, follow these steps:
```

$ cd ~
$ cd .mozilla
$ ls 
listing of files; look for "something.default"
$ cd something.default
$ ls -a
listing of files; look for .parentlock
$ rm .parentlock

```

---

### Post by Navneet_Kumar on 2014-03-28
As an alternative try using the latest version of firefox anx preferably run it from the terminal with sudo privilages.I hope it will automatically sort out the problem.

---

### Post by varunendra on 2014-03-28
> **Navneet_Kumar said:**
> As an alternative try using the latest version of firefox anx [COLOR="#FF0000"]**preferably run it from the terminal with sudo privilages**[/COLOR].I hope it will automatically sort out the problem.

**NEVER** run any browser with root privileges!! That is an open invitation to the bad guys/things on the Internet to intrude, conquer and rule your system within minutes if not seconds!

Doesn't mean it will happen immediately, but with a browser running as root, your system is just as secure as a fat rabbit surrounded by a pack of wolves.

---

### Post by SeijiSensei on 2014-03-29
Besides if you ran Firefox with root privileges, it would be using root's profile in /root/.mozilla.  That wouldn't help with a problem in the user's own profile.

Just delete the .parentlock file.  It's a pain in the neck, but it does solve the problem.

---

