---
title: "Scripting help"
date: 2008-03-04
forum: General Help
---

### Post by msjones on 2008-03-04
Hi,

I have started writing simple scripts for boring tasks. I would like to write a search script to save me entering sudo find . -name "*filename*" -print

my script is as follows:

```

#!/bin/bash

# This is a script to search for files from /

clear

cd /

echo "Enter filename to search for:
> \c"

read FILENAME

sudo find . -name "$FILENAME" -print
```

As you can see i would like it to pause so i can enter the filename. after I do this i press return and it just takes me back to prompt.

also it displays the > \c in stead of blank space for entering my filename.

What am i doing wrong??

Thanks

---

### Post by jmpurser on 2008-03-04
A little off topic but you might want to check out the locate and updatedb commands rather than write a new script.

You also might want to use "echo -e" to interpret backslash escapes.

Luck,

John

---

### Post by msjones on 2008-03-04
Thanks for the reply! I have sorted it. The new script is:

> #!/bin/bash

# This is a script to search for files from /
clear
echo "
Enter filename to search for:"

read FILENAME

echo "Searching for file(s)"

sudo find / -name "$FILENAME"

Thanks!

---

### Post by noynac on 2008-03-15
Please delete

---

### Post by ghostdog74 on 2008-03-15
you don't even need a script at all. once you get familiar with the find command and its common options, you will be able to type them out and use them in a blink of an eye.

---

