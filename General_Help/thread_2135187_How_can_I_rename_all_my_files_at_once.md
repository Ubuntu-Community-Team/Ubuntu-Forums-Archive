---
title: "How can I rename all my files at once?"
date: 2013-04-13
forum: General Help
---

### Post by alcatraz678 on 2013-04-13
Hello,

I have bunch of image files that have _mini.jpg at the end. Ex: lorem_mini.jpg. Hundreds of files that have that suffix. I want to remove _mini but preserve its extension. How can I do that in command line?

---

### Post by schragge on 2013-04-13
```
rename -v 's/_mini(.jpg)$/$1/' *.jpg
```

---

### Post by dave0109 on 2013-04-13
Removed, as I see you've had a solution.

---

### Post by prodigy_ on 2013-04-13
To find and rename recursively:

```
#!/bin/bash

# replace /path/to/folder with actual path and folder name
find /path/to/folder -type f -iname '*_mini.jpg' -print0 | \
	while read -r -d $'\0' full_path; do
		mv "$full_path" "${full_path%_*}.jpg"
	done
```

---

### Post by alcatraz678 on 2013-04-13
it worked. :) thats a scary looking command. thanks!

---

