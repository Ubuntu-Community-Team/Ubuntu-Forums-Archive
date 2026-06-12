---
title: "distinguish what programs start on boot"
date: 2017-07-12
forum: General Help
---

### Post by marchello_lippi2 on 2017-07-12
Hi all, 

How do I distinguish what programs start on boot? 

```
$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
```

---

### Post by marchello_lippi2 on 2017-07-12
Installed boot-up manager
> sudo apt-get install bum
ran it 
> sudo bum
I was able to see some services that I've needed to stop from running on boot. Though the list is not full. 
What else should I check to see complete list?

---

### Post by marchello_lippi2 on 2017-07-12
For example, I can see sqlservr (mssql for linux) in top. I did not run it manually. I was not able to see it using bum. 
Where I can see sqlservr and disable it from running on boot? I would rather not remove it completely so far.

---

### Post by marchello_lippi2 on 2017-07-12
I was able to stop not needed services (which I would rather not remove completely so far) until next boot: 
> sudo service mssql-server stop; sudo service mysql stop
How do I stop them from running on boot? I would rather run them manually on demand. 
Please advise.

---

### Post by &amp;KyT$0P# on 2017-07-13
Does the [FONT=Courier New]systemctl disable[/FONT] command do what you want?

**Note:** That is not an exact command to run.  Refer to [FONT=Courier New]man systemctl[/FONT] for more info.

---

### Post by marchello_lippi2 on 2017-07-13
[[COLOR=#000000]halogen2[/COLOR]]("https://ubuntuforums.org/member.php?u=2034672")
Ran it, will see on my next boot, thx.

---

### Post by marchello_lippi2 on 2017-07-14
[[COLOR=#000000]halogen2[/COLOR]]("https://ubuntuforums.org/member.php?u=2034672")
thx, [COLOR=#000000][FONT=&quot]systemctl disable [/FONT][/COLOR]worked for me.

---

### Post by &amp;KyT$0P# on 2017-07-14
You're welcome.

---

