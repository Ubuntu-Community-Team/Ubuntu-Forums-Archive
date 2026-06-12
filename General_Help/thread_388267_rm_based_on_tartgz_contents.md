---
title: "rm based on tar/tgz contents"
date: 2007-03-19
forum: General Help
---

### Post by Timtro on 2007-03-19
Hi all,

I recently expanded a LaTeX package into my texmf tree. Anyhow, it has some freakish consequences, and now I need to remove it.

Rather than tracking down the files, what is the simple way for me to remove the files? I assume that there is some what to use the file tree from the tar (or tgz) to selectively remove files.

Thanks.

EDIT------------

Come to think of it, it may have been a zip file! Although I could easily convert.

---

### Post by mbeierl on 2007-03-19
Presuming your tar file is called "your-tar.tgz", you could try something like this:
```

for file in `tar tzvf your-tar.tgz | cut -d: -f2 | cut -c4-`; do rm $file ; done

```
What this does is lists the output from the tar (option t), and pipes it to cut.  The first cut command strips off most of the extra file input by using the ":" in the timestamp.  The second cut command removes the rest of the timestamp, leaving just the filename.

Something similar can be done using unzip -l.

Of course this only works if there are no spaces in the filename.  If there are, you'll need to use sed or something to mask them.  Let me know if that's the case, or if you need help with zip.

---

