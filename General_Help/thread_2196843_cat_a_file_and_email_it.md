---
title: "cat a file and email it"
date: 2013-12-31
forum: General Help
---

### Post by TheFuzz4 on 2013-12-31
So I have a script here
```

#!/bin/bash

mailto="email@email.com"
subject="New Files Added To mydomain Over The Last Week"
newfiles=`cd Files && find . -type d -mtime -7 > ~/filelist.txt`
filelist="`cat filelist.txt`"
body="The following new files were added to the share over the course of the last week "${filelist}""



echo ${body} | mail -s "${subject}" ${mailto}

```

The problem I'm having with my script is that when it generates the email and shoots it out, the email has everything all on one continuous line.  What I would like it to do is when it cats the file to put the output of the file on individual lines.  Thank you all in advance for your assistance with this.  I also apologize if this should be in a different subforum.

---

### Post by erind on 2014-01-01
I'd do it slightly differently:

```
#!/bin/bash

mailto="email@email.com"
subject="New Files Added To mydomain Over The Last Week"
echo "The following new files were added to the share over the course of the last week:" > ~/filelist.txt
cd Files && find . -type d -mtime -7 >> ~/filelist.txt

mail -s "${subject}" ${mailto} < ~/filelist.txt
```

There needs to be quoting around *${body}* in your script to preserve the newlines, but it's still best to read the file as shown above ( *mail -s ... < ~/filelist.txt *), where newlines are always preserved.

---

### Post by TheFuzz4 on 2014-01-02
Ah so simple and yet I overlooked it by trying to over complicate it.  Thanks for your suggestion it works like a champ.

---

