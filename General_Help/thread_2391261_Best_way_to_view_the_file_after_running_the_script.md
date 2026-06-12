---
title: "Best way to view the file after running the script command"
date: 2018-05-07
forum: General Help
---

### Post by Sherman_Willden on 2018-05-07
Name: Sherman
Desktop: HP Compaq 6710b
UBUNTU: 18.04 new install

I use the script -a command to capture my updates and installs. Of course the generated file has several unwanted characters in it. In the long-ago past on UNIX I used some type of reader to see the file as a plain ascii file without all the garbage. Does anyone remember that utility? Also how do you capture your updates and installs. It may be already captured within the UBUNTU apt file system.

Thank you;

Sherman

---

### Post by steeldriver on 2018-05-07
The `less` pager should be able to display script output correctly (including terminal colors)

---

### Post by HermanAB on 2018-05-07
less, more, head, tail, nano, pico, vi, emacs, geany, gedit, leafpad...

I would use nano.

---

### Post by deadflowr on 2018-05-07
> It may be already captured within the UBUNTU apt file system.
They are,
in the apt log files in
/var/log/apt and if auto updater enabled (unattended-upgrades) /var/log/unattended-upgrades
and also the dpkg log in /var/log/dpkg.log
These log files are all rotated after X amount of time so beyond just the regular log files you'll also have several zip/tar archives of past logs as well.

---

### Post by again? on 2018-05-08
```
cat /path/to/capture/file
```

---

