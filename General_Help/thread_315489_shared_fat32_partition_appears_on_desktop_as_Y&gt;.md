---
title: "shared fat32 partition appears on desktop as Y&gt; &lt;/HTML&gt;"
date: 2006-12-09
forum: General Help
---

### Post by chochem on 2006-12-09
As the title says, my shared partition appears on the desktop and in nautilus with the somewhat strange name "Y> </HTML>". It does however respond to adresses containing "/media/hda5/" so I guess it is mounted as such (following a 6.10 install I can no longer find the "Administration" item referred to simply as "Disks" that allowed for GUI mounting and dismounting). I can see the option rename on the context menu but it's greyed out (root user privileges?). 

Any help appreciated.

P.S. The installation was a bit hurried so I forgot setting ubuntu up to mount the windows partition as 'windows' and the above mentioned as 'shared' - how do I change that permanently?

---

### Post by taurus on 2006-12-09
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Don't forget to create the new mount points or they won't be mounted...

---

### Post by chochem on 2006-12-11
Thanks - seems to have done the trick :)

BTW: Where did "Disks" go? Has it been moved/renamed/replaced in 6.10 or has it been rendered obsolete? Or can I get from universe (and if so, under what name?)

---

