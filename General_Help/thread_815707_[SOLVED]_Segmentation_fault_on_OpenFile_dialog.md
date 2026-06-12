---
title: "[SOLVED] Segmentation fault on OpenFile dialog"
date: 2008-06-01
forum: General Help
---

### Post by VictorR on 2008-06-01
Recently I faced the problem with "non-native" GTK applications - when trying to display OpenFile dialogue (or how it is called) some apps, like GIMP or Swiftfox, crash with Segmentation fault error.
```
victor@ubuntu-desktop:~$ gimp
Failed to connect to socket /tmp/dbus-AqCCZFNFWG: Connection refused

(script-fu:3372): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault
victor@ubuntu-desktop:~$ swiftfox
Segmentation fault
victor@ubuntu-desktop:~$ 

```
It does not happen with "native" Gnome programs (as far as I know both GIMP and Swiftfox (Firefox) use some extra graphic libraries).
There was a post about similar problems two month ago:
[http://ubuntuforums.org/showthread.php?t=763627&highlight=segmantation+fault](http://ubuntuforums.org/showthread.php?t=763627&highlight=segmantation+fault)
but with no solution.

Any ideas?

---

### Post by VictorR on 2008-06-01
Oops! I was wrong. Just checked GEdit and got the same issue.
```
victor@ubuntu-desktop:~$ gedit  (now I click "Open")
Segmentation fault
victor@ubuntu-desktop:~$

```
Some programs work, others don't.

The system: Ubuntu 8.04 (upgraded from Gutsy),  Linux ubuntu-desktop 2.6.24-17-generic.

---

### Post by VictorR on 2008-06-01
The problem disappeared itself, after I had rebooted the computer. Seems it was hardware-related issue.

---

