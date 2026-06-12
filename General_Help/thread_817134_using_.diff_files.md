---
title: "using .diff files"
date: 2008-06-03
forum: General Help
---

### Post by frogitts on 2008-06-03
Just a basic understanding/using question. I use Digikam with Kipi plugins, but the plugin for uploading to picasa web albums doesn't work. Someone wrote a patch for this in a file called picasawebexport_patch.diff (which can be found here: [http://hatred.homelinux.net/~hatred/picasawebexport_patch.diff](http://hatred.homelinux.net/~hatred/picasawebexport_patch.diff)). I want to know how to apply this patch, assuming it is one, because it looks to my unknowing eyes like a list of changes between files, not a patch. Can anyone give me a hint?

---

### Post by bingoUV on 2008-06-03
A patch is exactly a list of changes. See manual page of patch (below command). Backup the original file before making changes. Generally the place where you find the patch tells you about exact procedure to apply the patch.
```

man patch

```

---

