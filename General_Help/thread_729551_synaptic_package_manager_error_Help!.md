---
title: "synaptic package manager error Help!"
date: 2008-03-20
forum: General Help
---

### Post by tony2tone on 2008-03-20
Hi Newbie here
Got an error with synaptic Package manager after a failed download of google desktop
  
error I'm getting is:
E: Type '<!DOCTYPE' is not known on line 1 in source list  /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

need help please. TNX:confused:

---

### Post by Bubba64 on 2008-03-20
It looks like you need to add the mediubuntu repository here is a link, also save this link page because there is a ton of good instructions you might need for yourself or to help others the search bar is the answer or hopefully leading to one.
[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)

---

### Post by kesman on 2008-03-20
You have a typo in your /etc/apt/sources.list edit it with 
```

sudo nano /etc/apt/sources.list

```

---

### Post by plucky on 2008-03-20
> E: Type '<!DOCTYPE' is not known on line 1 in source list **/etc/apt/sources.list.d/medibuntu.list**

The error is not in **/etc/sources.list** but in **/etc/apt/sources.list.d/medibuntu.list**.
That is the file you need to correct.

Good Luck

edit: Found this [thread](http://ubuntuforums.org/showthread.php?t=729550)

---

### Post by tony2tone on 2008-03-20
Thanks To all your replies

I tried researching about this problem but couldn't find the solution so I just reinstalled my OS, but thanks anyway. Ubuntu is just great:)

---

