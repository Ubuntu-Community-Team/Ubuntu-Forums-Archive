---
title: "synaptic package manger crashed"
date: 2007-04-04
forum: General Help
---

### Post by Quartlow on 2007-04-04
I was trying to install virtual box. It crashed during the install. now i get an error message from the update manger saying
.
> 'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

Synaptic says
> 
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Is there a config file somewhere I can edit to get rid of this error message?

---

### Post by spankymasterc on 2007-04-05
Error

E: The package virtualbox needs to be reinstalled, but I can&#8217;t find an archive for it.

-:::Package name in the above error could be any package:::-

Solution

Run the following command

For virtualbox Pakage

dpkg --remove --force-remove-reinstreq virtulbox

---

### Post by Quartlow on 2007-04-05
That didn't work, Returned this message

> dpkg - warning: ignoring request to remove virtulbox which isn't installed.

---

### Post by zvacet on 2007-04-05
```
sudo apt-get remove --purge program_name
```

---

### Post by Quartlow on 2007-04-05
that didn't work either

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by Quartlow on 2007-04-05
I just thought of this, in case anyone ask's the package is still on the desktop. I even tried deleting it and downloading it again

---

### Post by Quartlow on 2007-04-06
bump, come on somebody has to have an idea here. 
there has to be a way.
Some where the package manager and the update manger have to have a file to reference. If I can locate that file and edit it manually to remove the reference to virtual box, hopefully the problem goes away. 

The only other alternative I see at this point is a complete reinstall. Not really a biggie was just trying to avoid it

---

### Post by zvacet on 2007-04-06
```
whereis file_name ls
```

---

### Post by Quartlow on 2007-04-06
```
file_name:
ls: /bin/ls /usr/share/man/man1/ls.1.gz
```

Ok, so whats that tell us?

---

### Post by Quartlow on 2007-04-08
Bump

---

### Post by ramjet_1953 on 2007-04-08
As a last resort, try this:

Code:

[COLOR="Red"]sudo gedit /var/lib/dpkg/status
[/COLOR]
Do a search in this file for the recalcitrant package (in this case VirtualBox) and CAREFULLY delete the entry.

Save the file

Code:

[COLOR="Red"]sudo apt-get update[/COLOR]

This should fix the problem and Synaptic should be happy again.

Regards,
Roger :cool:

---

### Post by gjohn2 on 2007-04-21
Worked for me, thanks.

---

