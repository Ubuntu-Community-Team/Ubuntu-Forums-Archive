---
title: "ProFTPD Jail and a super user/group"
date: 2014-03-07
forum: General Help
---

### Post by rackit on 2014-03-07
Using ProFTPD I have my users jailed to thier home via ftp and a group that can traverse all directories. I want to jail this group to /home though so members of it can't get into the rest of the file system. Any suggestions as to how I can make that happen? 

Here is the line from my proftpd.conf:

```

# Use this to jail all users in their homes 
DefaultRoot                  ~ !ftp-super


```

---

