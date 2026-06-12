---
title: "setting permissions"
date: 2006-12-29
forum: General Help
---

### Post by nuts11222 on 2006-12-29
I'm fairly new to linux, but am loving it so far. I keep getting the messege below ! I know I screwd up my synaptic setting and seem to fix them.

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Thanks
Andrew:rolleyes:

---

### Post by pay on 2006-12-29
As it says, check your /etc/apt/sources.list.```
cat /etc/apt/sources.list
```and post the output. The permissions should be ```
sudo chown root:root /etc/apt/sources.list
``` I think... I maybe wrong, i don't even use Ubuntu:P

---

### Post by johnnymac on 2006-12-29
Make sure your settings are as follows:

```

ls -la /etc/apt/sources.list
-rw-r--r-- 1 root root 2506 2006-12-28 21:52 /etc/apt/sources.list

```

if not you can issue the following
```

sudo bash

```

if the actual permissions aren't correct (ie, not -rw-r--r--)
```

chmod 644 /etc/apt/sources.list

```

if the actual ownership isn't correct (ie, root root)
```

chown root:root /etc/apt/sources.list

```

Hope this helps...

---

