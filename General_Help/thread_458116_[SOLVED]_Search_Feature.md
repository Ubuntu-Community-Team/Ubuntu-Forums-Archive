---
title: "[SOLVED] Search Feature"
date: 2007-05-29
forum: General Help
---

### Post by Zeotronic on 2007-05-29
Recently I installed mtPaint from GetDeb... I was going to make it one of the programs that appears on the right-click menu for it's supported file formats, but I can't find it... If someone could tell me where it is,that would be great, but I realize that Xubuntu 7.04 doesn't seem to have a search function (one that I can find anyways)... all it seems to have is appfinder, which appears to be totally useless. I'm sure there are but are there any search programs out there?.. like Windows' search function.

---

### Post by Pragmatist on 2007-05-29
> **Zeotronic said:**
> ...are there any search programs out there?.. like Windows' search function.

Install Beagle (note the comment about using "kerry" with xubuntu):

[https://help.ubuntu.com/community/Beagle](https://help.ubuntu.com/community/Beagle)

If you want to use the command-line, you can do this:

First you create a database of your files with this command (it takes a few minutes the first time you run it):
```
sudo updatedb
```

Now you can use the "locate" command to find what your looking for:

```
locate mtpaint
```

If you are just looking for the executable, most likely it is in a directory labeled "bin" (for binary).  So, use the "grep" command to filter your results:

```
locate mtpaint | grep bin
```

---

