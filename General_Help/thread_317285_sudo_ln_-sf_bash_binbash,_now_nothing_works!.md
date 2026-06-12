---
title: "sudo ln -sf bash /bin/bash, now nothing works!"
date: 2006-12-12
forum: General Help
---

### Post by Xecuter on 2006-12-12
I followed [this guide to installing the ATI-drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually") and I got to this point:
> Create .deb packages:

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh


I then managed to write sudo ln -sf bash /bin/bash. Now nothing works. All I'm getting is an error: "ln: accessing «/bin/bash»: Too many levels of symbolic links"

How can I fix this? Please help!

BTW: I'm using Edgy. Where do I fix the thing that says what I'm using?

---

### Post by halfvolle melk on 2006-12-12
You could try to
```
sudo dpkg-reconfigure dash
```

---

### Post by engla on 2006-12-12
Let us know your current situation. Tell us what "ls -l /bin/sh /bin/bash /bin/dash" says

> **Xecuter said:**
> 
BTW: I'm using Edgy. Where do I fix the thing that says what I'm using?

Go to the "User CP" in the bar above, and look on the bottom of the "Edit Profile" page.

---

### Post by Xecuter on 2006-12-12
> **engla said:**
> Go to the "User CP" in the bar above, and look on the bottom of the "Edit Profile" page. Thanks! :D

Firstly, when I did it i couldn't run anything, not even a terminal.
Secondly, I fixed it by copying the bash-file from the Ubuntu 6.10 Live-CD.

But thanks anyways for answering! :D

---

