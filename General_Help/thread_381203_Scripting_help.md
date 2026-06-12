---
title: "Scripting help"
date: 2007-03-10
forum: General Help
---

### Post by Matt1632 on 2007-03-10
I'm trying to make a script to upload files to an ftp server, to update a website.  I'm a little stuck, here's what I have so far.
```

#!/bin/bash
# Website update script
cd Website(This is the directory with the files I want to copy.)
ftp ftp.servername.com
put index.html 
put about.html
put calendar.html
put contact.html
put schedule.html

```
However, it doesn't execute the put commands until I manually exit the ftp server, how can I fix this?

---

### Post by antek on 2007-03-10
Create a new file, name it for example "commands", and put the "put" commands there. Then invoke ftp as:

```

cat commands | ftp -

```

and it should work. Also consider using lftp instead. lftp has a nice "-e" command, which allows you to specify the commands to perform on another server via the command line, f.e.:

```

lftp -e 'open some_site; put file1; put file2; bye'

```

Hope this helps.

---

