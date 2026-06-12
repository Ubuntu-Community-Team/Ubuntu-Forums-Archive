---
title: "cannot execute binary file"
date: 2012-11-09
forum: General Help
---

### Post by woodyg on 2012-11-09
I have a file that can be executed by double-clicking it,  but when trying to execute it command line, it doesn't work. I get "**cannot execute binary file**"

```
ml@ThinkPad-Edge:~/arkivdigital$ dir
adclient2_en_US.qm  arkivdigital-online  license_en_us.html
ml@ThinkPad-Edge:~/arkivdigital$ bash arkivdigital-online
arkivdigital-online: arkivdigital-online: cannot execute binary file
ml@ThinkPad-Edge:~/arkivdigital$ 
```What am I doing wrong?

---

### Post by LordXandor on 2012-11-09
> 
ml@ThinkPad-Edge:~/arkivdigital$ bash arkivdigital-online

Instead cd to the directory the file is located and run the command:
```
./arkivdigital-online
```

The ./ tells it to run the file from the current directory.

---

### Post by woodyg on 2012-11-09
Thanks, it's working now :)

---

