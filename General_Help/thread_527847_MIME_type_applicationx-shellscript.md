---
title: "MIME type: application/x-shellscript"
date: 2007-08-17
forum: General Help
---

### Post by mic520 on 2007-08-17
When I  edited file by nano editor, the MIME type: text/plain is a default one for newly created file. Although, when I run the file the error shows that the bash compiler doesn't recognize it as application. When I open old script with MIME type: application/x-shellscript, and just change the text to new sript, everything OK. But this way is too annoying. Is there a way to set MIME type for file when created by editor?

---

### Post by jamvegan on 2007-08-18
As far as I know, the mime type is determined on-the-fly.  I just created a simple shell script in nano, and the Properties window shows that its mime-type is application/x-shellscript.  When you write your scripts do you start them with either of the following?
```
#!/bin/bash
#!/bin/sh
```
One of those should be at the absolute beginning of the file (no blank line or even space before the #) for bash to recognize the file as a shell script.  You also need to add execute permission to the file to be able to run the script from the command line.

Hope this helps!

---

