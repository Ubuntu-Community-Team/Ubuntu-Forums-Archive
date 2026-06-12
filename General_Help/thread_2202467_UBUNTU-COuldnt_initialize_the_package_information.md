---
title: "UBUNTU-COuldnt initialize the package information"
date: 2014-01-29
forum: General Help
---

### Post by amar3 on 2014-01-29
i am a newbie to ubuntu.following is the screen shot,which i am getting error for..


[IMG]http://i58.tinypic.com/wrcpqx.png[/IMG]

---

### Post by Bashing-om on 2014-01-29
amar3; Hi ! Welcome to the Forum .

We often see this condition as a result of corrupted controls files. 
Solution; Remove the files and regenerate a new data base>
Terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Then advise us of the result.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

