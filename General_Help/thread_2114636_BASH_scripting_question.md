---
title: "BASH scripting question"
date: 2013-02-10
forum: General Help
---

### Post by gachnar on 2013-02-10
I've been puzzling over this for quite some time and am having no luck.

I've got some files with the following format "[XXXXX] SHOW / NAME - ## [MD5-HASH].mkv"

I can successfully use sed to replace the SPACES, but the "/" I can't get it removed. I've tried all kinds of ways to escape it changing the default sed delimiter and about everything else i can think of... No Joy. Can someone tell me how I might be able to do this?

---

### Post by Habitual on 2013-02-10
```
sed -e 's/\///g
``````
cat /proc/swaps                   
Filename                Type        Size    Used    Priority
/dev/sda2                               partition    1984020    600    -1

cat /proc/swaps | sed -e 's/\///g'
Filename                Type        Size    Used    Priority
devsda2                               partition    1984020    600    -1

```

---

### Post by gachnar on 2013-02-10
Ok... apparently really a noob here... the file was a "&#8260;" not a "/" if that's not quite clear... it looks like a forward slash, but actually isn't. Once I copied and pasted it, that seems to have cleared it up.... 

can someone perhaps give me a clue what that one is called?

---

### Post by diesch on 2013-02-10
"&#8260;" is called "fraction slash"

---

### Post by Vaphell on 2013-02-10
standard forward slash can't exist in filenames because it is used in paths - you wouldn't be able to distinguish between file/name and dir/filename

---

### Post by schragge on 2013-02-10
> **gachnar said:**
> changing the default sed delimiter
Works with me
```

[COLOR=green]$[/COLOR] sed 's:^[[][^]]*] \(.*\) / \(.*\) -.*:\1_\2.mkv:' \
[COLOR=green]>[/COLOR] <<<"[XXXXX] SHOW / NAME - ## [MD5-HASH].mkv"
[COLOR=green]SHOW_NAME.mkv[/COLOR]

```

Please ignore this, didn't see your post about fraction slash

---

