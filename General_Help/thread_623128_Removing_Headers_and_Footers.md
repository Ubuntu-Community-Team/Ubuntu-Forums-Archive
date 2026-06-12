---
title: "Removing Headers and Footers"
date: 2007-11-25
forum: General Help
---

### Post by Uiop on 2007-11-25
How would I remove similar (but not identical) headers and footers from hundreds of HTML files that are stored in many subdirectories.  I'm a bit of a Linux beginner, but I think that the find command coupled with some other regex search and replace command would do the trick.  Any ideas?

Here's an example:
```

<html>
<head>
<title>[Unique page text.]</title>
[Text that is identical in all files.]
</head>
<body>
[Unique page text.]
[Text that is identical in all files.]
</body>
</html>

```

It should become:
```

[Unique page text.]

```

Any help would be greatly appreciated!

---

### Post by nick_h on 2007-11-25
In general you could approach a problem like this in 2 stages.  Firstly, write a shell script that takes a filename as a single parameter that strips out the required text.  Then, as you suggested, call this script from a find command as follows:
```
find . -name "*.html" -exec ~/script.sh '{}' \;
```
This assumes that you search for html files from the current directory and the script is in your home directory.

If the [Unique page text.] in the title is the same as that in the body and is on a single line then the problem is easy.  Just use grep to find the line required and sed to remove the tags.

I expect that the [Unique page text.] in the body is different from the title and not a single line.  In this case use awk in a script similar to:
```
awk '/<\/body>/ {x=0} \
    {if (x) print $0} \
    /<body>/ {x=1}' "$1" > "$1".new
```
This will take everything in the body and put it in a new file.  You will have to modify it but it will give you the idea.

---

