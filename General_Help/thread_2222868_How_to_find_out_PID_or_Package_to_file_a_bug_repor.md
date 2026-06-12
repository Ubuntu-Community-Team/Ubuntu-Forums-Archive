---
title: "How to find out PID or Package to file a bug report?"
date: 2014-05-08
forum: General Help
---

### Post by Katzwinkel on 2014-05-08
Hi,
I want to file a bug report about [this issue]("http://ubuntuforums.org/showthread.php?t=2220855") that seeminlgy cannot be resolved.

However, i need to state a Package or PID in order to file such a report. SInce it is not about a crash or anything, but about the fact that some hardware (my WiFi-card) is constantly hardblocked in Linx (and ONLY in Linux), I don't have any specific PID and have no idea how to find out the appropriate Package.

Running "ubuntu-bug" is supposed to lead me through a series of questions to determine the problem, but since my Problem is not related to Dislay, storage devices, security, sound or similar, I can only choose "other problem". And that leads to the response that I need to state a PID or package.

---

### Post by ian-weisser on 2014-05-08
Take a look at  [http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill](http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill)  for a couple possible solutions to your rfkill issue.

If not, then file the bug against the 'linux' package.

---

### Post by Katzwinkel on 2014-05-09
thanks, "Linux" package was what I needed.

---

