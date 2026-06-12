---
title: "Error while trying to run &quot;sudo apt-get update&quot;"
date: 2016-05-31
forum: General Help
---

### Post by jsvidyad on 2016-05-31
Hello,

    I'm running ubuntu 14.04.4 LTS. When I run the command 
sudo apt-get update
in order to update my system, I get the following error message at the very end of the resulting output:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


I have been seeing this error message since this past Sunday (May 29, 2016). Can someone please help me fix this error?

---

### Post by Bashing-om on 2016-05-31
jsvidyad; Hello;

Since "  past Sunday (May 29, 2016).  "
 I would think if it were a syncing issue with the mirror that it would have caught up by this time.
Let us suppose there is a corruption issue in your lists files.
We can remove the files and the system will rebuild with current info:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```
upon the update.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

