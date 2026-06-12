---
title: "how to send an email if a folder is modified"
date: 2015-04-15
forum: General Help
---

### Post by sohlinux on 2015-04-15
Hi,

I want to get an email alert if a certain folder is modified but how do I pipe the output from the command so it sends an email not just show the changes to the folder in the terminal?

something like the following...

```
#!/bin/bash
inotifywait -m /home/tom -e create -e moved_to |
    while read path action file; do
        echo "The file '$file' appeared in directory '$path' via '$action'"
/usr/bin/Mail -s "notify" "email@12345mail.com"
    done
```

---

