---
title: "wget servername as directory"
date: 2014-02-25
forum: General Help
---

### Post by chris137 on 2014-02-25
Hi,
I'm using wget to backup my data on my FTP-server as follows:
```
#!/bin/sh
date=$(date +"%d-%b_%H-%M")
wget -rq --user=myuser --password=mypswd ftp://server.net/ -P /home/chris/backup/$date
```
Example:
The file text.txt in the main dir of the server should be found there: /home/chris/backup/24-Feb_17-59/text.txt
In my case I will find it here:  /home/chris/backup/server.net/24-Feb_17-59/text.txt

I have absolutely no clue why. I'm pretty sure I'll just need another operator or so but I just won't find a solution.

Any help?

---

### Post by Vaphell on 2014-02-25
maybe this?
```
 -nH, --no-host-directories      don't create host directories.
```

either way you can try downloading stuff to a fixed path and rename the dir afterwards with mv.


I have my doubts about the dir name format, it doesn't lend itself to chronological sort in case you need it.
Also consider using $HOME instead of hardcoded /home/chris, it expands to the same thing but is much more portable

---

### Post by chris137 on 2014-02-25
Thanks, that's it!
I gues moving it afterwards would only complicate all that.
Everything's fine now, thanks for your help!

---

