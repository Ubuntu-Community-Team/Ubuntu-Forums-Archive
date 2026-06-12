---
title: "[SOLVED] script to open  file browser"
date: 2008-03-27
forum: General Help
---

### Post by amin_inb on 2008-03-27
Hi,

I need a script witch open a file browser to let user select file then return path

any one can help ?

---

### Post by pointone on 2008-03-27
What programming language?

---

### Post by jpeddicord on 2008-03-27
For any Bash or shell script:

```
zenity --file-selection
```

That returns the selected file to STDOUT/terminal. For more options, run the following command:

```
zenity --help-file-selection
```

---

### Post by amin_inb on 2008-03-27
#!/bin/bash
.....

---

### Post by amin_inb on 2008-03-27
zenity --file-selection works, thnks

any example to put it's output for gedit (edit selected file with gedit) ?

---

### Post by jpeddicord on 2008-03-27
> **amin_inb said:**
> #!/bin/bash
.....

Yep.

```
#!/bin/bash

zenity --file-selection
```

That is the basic way to use it in a script, though it won't do much.

(Edit, too late!)

---

### Post by jpeddicord on 2008-03-27
> **amin_inb said:**
> zenity --file-selection works, thnks

any example to put it's output for gedit (edit selected file with gedit) ?

```
zenity --file-selection | xargs gedit
``` :)

---

