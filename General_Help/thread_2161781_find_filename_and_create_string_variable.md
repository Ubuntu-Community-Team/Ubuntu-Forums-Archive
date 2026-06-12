---
title: "find filename and create string variable"
date: 2013-07-11
forum: General Help
---

### Post by TrenTech on 2013-07-11
So I'm relativity new to bash scripting. I've dabbled a bit but nothing too complex. So the scenario is I'm currently hosting a minecraft server for the community. It's heavily modded so sometimes bad things happen, In particular sometimes it crashes and freezes up to the point where killing the process is the only way to recover. Originally I wrote a script that would pgrep for a partial of the filename and kill the process. Now however I have multiple instances running so this will not work. Because of frequent updates I cannot do an exact name. So what I am looking for is a way to find the jar file in a particular directory and create a string variable of the filename so I can pgrep the exact name. so far I've come up with:

find '/path/to/jar/' -name 'partial-name*'

This works however shows the path as well, where I just need the file name. Hoping someone can help me out, point me in the right direction.

---

### Post by steeldriver on 2013-07-11
try

```
find '/path/to/jar/' -name 'partial-name*' **-printf '%f\n'**
```

Or you could take the whole thing, and trim off the path with shell substitutions e.g.

```

$ f="./path/to/a/file"
$ echo "${f##*/}"
file

```

---

### Post by TrenTech on 2013-07-11
Cancel that. I figured out a better way to kill the processes by identifying the SCREEN they're attached to and terminating it, thus keeping from accidentally killing the wrong process. I got to thinking there would be cases where some  processes would have the same file-name depending on when they updated, causing multiple PID's to display. The screen's they are attached to are unique to each instance so that resolves the problem. Thanks for the help though!

---

