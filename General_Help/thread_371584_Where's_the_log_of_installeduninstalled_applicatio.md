---
title: "Where's the log of installed/uninstalled applications?"
date: 2007-02-27
forum: General Help
---

### Post by velvetGreen on 2007-02-27
I cleaned yesterday my orphan packages by installing and running a third party application called 'system-upgrade' in konsole, I seemed to clean some sound specific programs as well as noticed this morning my system can't produce any sounds (kde).

Is there a log of some sort that let's me check what packages were removed? I checked the .bash_history.txt in my ~/ but that shows only the commands I've entered.

---

### Post by erkki70 on 2007-02-27
Hi,
You may find some answers in this post:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
Hope it helps...

---

### Post by velvetGreen on 2007-02-27
Thanks for the tip, bookmarked it even but it really doesn't help with this now.

What I need to know is what I uninstalled yesterday in order to revert the changes. For that I need to know the output of bash, or find a log of some sort that tells what packages I've installed/uninstalled.

**Edit:** I checked the /var/logs/ more carefully and found 'dpkg.log' that showed everything I've done for packages. I installed the ones I removed yesterday and sounds are working again.

---

