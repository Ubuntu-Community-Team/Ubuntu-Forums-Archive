---
title: "deb packages error"
date: 2007-11-24
forum: General Help
---

### Post by WhiteSlash on 2007-11-24
I can't install anything and my update manager doesn't work, it returns this error...

"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mercury-messenger needs to be reinstalled, but I can't find an archive for it.'" and then closes

Can someone help me?
By the way, synaptic manager doesn't work either.
[COLOR="Red"]
**UPDATE:**[/COLOR][B]
I finally fixed it!
I used this command
sudo dpkg --force all -r mercury-messenger
sudo dpkg --force all -r <theconflictingpackage goes here>
Thanks anyway :D[/B]

---

### Post by taurus on 2007-11-24
Open a terminal and post the outputs of these two commands.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by WhiteSlash on 2007-11-24
I did that, but it only gave me a similar response 
"Reading state information... Done
E: The package mercury-messenger needs to be reinstalled, but I can't find an archive for it."

---

### Post by WhiteSlash on 2007-11-25
I finally fixed it!
I used this command
sudo dpkg --force all -r mercury-messenger
sudo dpkg --force all -r <theconflictingpackage goes here>
Thanks anyway :D

---

### Post by louieb on 2007-11-25
WhiteSlash,  Thanks for posting how you fixed it.  
Have added it to my FAQ page. 
Lou

---

