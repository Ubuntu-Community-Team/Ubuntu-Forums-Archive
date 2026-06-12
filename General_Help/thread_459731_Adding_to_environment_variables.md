---
title: "Adding to environment variables???"
date: 2007-05-31
forum: General Help
---

### Post by andrew.46 on 2007-05-31
Hi,

 I am attempting to setup slrn and I am stuck in the early stages. I have the correct syntax for adding my news server to the environment variables:

```
NNTPSERVER='my news server' && export NNTPSERVER
```

 When I check (in the same Terminal window) printenv shows the variable has been neatly added. But after I close the Terminal window and open another window printenv shows the news server is no longer there. So, I can add it temporarily, to the shell that I have open, but I want to add it permanently!!

 I suspect that I am missing something here, although I certainly get it that slrn is a beast to set up :-)

              Thanks to anyone who can guide me,

                                   Andrew

---

### Post by Stephen Howard on 2007-05-31
Your theory is correct.  To make it permanent add the line to the end of the .bashrc file which will be in your home directory.  Bash reads this file each time it starts.

---

### Post by AZzKikR on 2007-05-31
And for system wide additions, edit the file /etc/profile.

---

