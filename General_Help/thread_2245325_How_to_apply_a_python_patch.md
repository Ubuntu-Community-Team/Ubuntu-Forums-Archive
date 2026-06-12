---
title: "How to apply a python patch?"
date: 2014-09-22
forum: General Help
---

### Post by AwaitingUserInput on 2014-09-22
I installed apt-offline from the repository, but when I tried to use it, I got an error. I searched and found a patch. See the OP [here]("https://bugs.launchpad.net/ubuntu/+source/apt-offline/+bug/1323976") for description and link to DL the patch.

So I downloaded the patch (filename: apt-offline.patch), then searched on how to install it.

What I read is that you can only patch source code, and not binaries. But since we're patching a python library (? - I think that's what it's called), does that rule apply? I think python libraries are in text, and not binary.

I tried overwriting the old /usr/share/pyshared/apt_offline_core/AptOfflineCoreLib.py file with the patch that I downloaded and got a new error.

```
$ sudo apt-offline set ~/Desktop/apt-offline.sig
Traceback (most recent call last):
  File "/usr/bin/apt-offline", line 25, in <module>
    from apt_offline_core.AptOfflineCoreLib import main
  File "/usr/lib/python2.7/dist-packages/apt_offline_core/AptOfflineCoreLib.py", line 1
    --- AptOfflineCoreLib.py.orig    2013-06-16 00:00:00.000000000 +0200
                                     ^
SyntaxError: invalid syntax

```

So my questions are, should I worry about this new error? Is there a better way to patch the python file?

---

### Post by steeldriver on 2014-09-22
You shouldn't have *overwritten* the file - you should have *patched* it. Unfortunately unless you made a backup you will probably need to re-install the apt-offline package in order to recover it. Then you can try this:

1. change to the containing directory
```

cd /usr/share/pyshared/apt_offline_core/

```

2. copy the patch file from wherever you have saved it e.g.
```

sudo cp ~/Desktop/apt-offline.patch ./

```

3. make a backup of the target file - just in case
```

sudo cp AptOfflineCoreLib.py{,.bak}

```

4. apply the patch
```

sudo patch < apt-offline.patch 

```

You should get a message like
```

patching file AptOfflineCoreLib.py
Hunk #1 succeeded at 1478 (offset -17 lines).

```

If you get a message with something like "hunk failed" then post back the details.

---

### Post by AwaitingUserInput on 2014-09-22
It looks like what you wrote worked correctly! I did indeed save a backup of the original library before overwriting, so I just put things back they way they were and did the patch the way you told me. I still have to actually do my updates with apt-offline, but so far, there are no errors and I'm optimistic. Thank you! I'll update once everything is done.

---

### Post by AwaitingUserInput on 2014-09-25
This worked properly. Thank you for the help!

---

