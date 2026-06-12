---
title: "Rename filenames in batch process"
date: 2008-01-11
forum: General Help
---

### Post by lce on 2008-01-11
I need to rename file names (in sub folders and sub sub folders) which contains a character.  I found the command **rename** but my problem is the character to escape is a **?**  (not unknown but the character ?)  Example: whatever?.pro

---

### Post by ghostdog74 on 2008-01-11
just put double quotes,eg
```

mv "whatever?.pro" "whatever-.pro"

```

---

### Post by capink on 2008-01-11
```
find "/path/to/the/folder/the/contains/the/subfolders" -type f -name '*\?*' | while read "file"; do newname=`echo $file | sed 's/\?//'`; mv "$file" "$newname"; done
```

Edit: This command will remove the '?' charachter from all files. So if this is not what you meant, do not run the command.

---

### Post by michaelzap on 2008-01-11
I just use GPRename for things like this.

---

### Post by kaiju on 2008-02-03
> **michaelzap said:**
> I just use GPRename for things like this.
well, i'd say capink's script is more useful for batch renaming as it is faster and, instead of processing just one directory at a time, it can actually do the renaming recursively ;)

---

