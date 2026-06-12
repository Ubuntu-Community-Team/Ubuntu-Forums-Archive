---
title: "How can I rename all *randomname*.jpg to Folder.jpg"
date: 2013-07-16
forum: General Help
---

### Post by keithy on 2013-07-16
> **prodigy_ said:**
> To find and rename recursively:

```
#!/bin/bash

# replace /path/to/folder with actual path and folder name
find /path/to/folder -type f -iname '*_mini.jpg' -print0 | \
	while read -r -d $'\0' full_path; do
		mv "$full_path" "${full_path%_*}.jpg"
	done
```

Cool script,

but I'm not clever enough to modify it for my needs!

I Have a directory structure with one random named .jpg per directory

I need to rename all *randomname*.jpg to Folder.jpg and leave it in the folder it was originally

Can anyone help??


Thanks

---

### Post by papibe on 2013-07-16
Moved to its own thread.

---

### Post by Vaphell on 2013-07-17
```
while read -rd $'\0' f
do
  p=${f%/*}   # trim shortest /* pattern on the right: /some/long/path[COLOR="#808080"]/file.jpg[/COLOR]
  d=${p##*/}   # trim */ longest pattern on the left: [COLOR="#808080"]/some/long/[/COLOR]path
  **echo** mv "$f" "$p/$d.jpg"
done < <( find . -iname '*.jpg' -print0 )
```

this will print out mv commands so you can check if everything is ok, if you like what you see and want to actually rename, remove *echo*.

---

