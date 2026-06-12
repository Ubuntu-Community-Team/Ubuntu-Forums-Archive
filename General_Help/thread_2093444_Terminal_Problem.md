---
title: "Terminal Problem"
date: 2012-12-10
forum: General Help
---

### Post by jgm4305 on 2012-12-10
I have a Pangolin Performance PAN06 laptop running Quantal. Up until recently I have always got Terminal running using my name... such as joe1234 laptop:... not the real name... that shows up when I connect to Terminal. 

Recently Terminal does not allow me to use a command but then comes back with a new name... joe1234@joe1234 laptop:... for example. It asks for a password but my real password does not work. 

What caused the double name?? How can I change Terminal back to the proper name and password??  

Thanks

---

### Post by papibe on 2012-12-10
Hi jgm4305.

Could you post the results of these commands?
```
id

groups

grep -i joe /etc/passwd

hostname
```
Regards.

---

