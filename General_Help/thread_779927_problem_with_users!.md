---
title: "problem with users!"
date: 2008-05-03
forum: General Help
---

### Post by helpineed on 2008-05-03
Hi i have created an unwanted user by accident and i have removed it from *System > Administration > Users and Groups*. but i need to remove the folder in the home folder(don't get confused im really stressed out).but i can't.


please help me!!

---

### Post by zvacet on 2008-05-03
```
sudo rm -r folder_name
```

---

### Post by HunterThomson on 2008-05-03
whenever I run into problems like that, I just boot up BackTrack3 from my USB Drive and from their I can access the hard drive and do anything I want. I bet you could just but up into any live cd and access the harddrive then go to the home folder and delete the user file and lost and found file. There must be a way to just do it in Ubuntu but what ever is EZ'r.

Have you tried the command line like this.

Sudo su
~/home/
ls
rm ((what ever the user file is called))

Ya do what zvacet said

---

### Post by helpineed on 2008-05-03
it said
```
rm: cannot remove `filename/.gvfs': Permission denied

```

---

### Post by HunterThomson on 2008-05-03
Ya, I am still having trouble with the permission stuff in Ubuntu too. That is why I just boot up into a traditional Linux environment to do stuff. I still don't know why I can bee logged in as root and ever see the phrase "Permission Denied".:confused:

Try the Ubuntu Live CD
But everyone should have a copy of BackTrack around anyway....

---

### Post by helpineed on 2008-05-03
anyway thanks for your help

---

### Post by HunterThomson on 2008-05-05
> **HunterThomson said:**
> whenever I run into problems like that, I just boot up BackTrack3 from my USB Drive and from their I can access the hard drive and do anything I want. I bet you could just but up into any live cd and access the harddrive then go to the home folder and delete the user file and lost and found file. Try the Ubuntu Live CD.


This will work for sure. I grantee it..... There is no need for the "thanks anyway". You should just say thanks.....:confused: I mean I know it is a weird way to delete the file's but it is fast and EZ.

---

