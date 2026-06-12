---
title: "Apt-get/Synaptic won't load..."
date: 2008-04-02
forum: General Help
---

### Post by whizkid515 on 2008-04-02
Whenever I try to load Synaptic, update manager, or try to install a package with apt-get, i get the following error message: 


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package conexant needs to be reinstalled, but I can't find an archive for it.'

Can anyone help me?:confused::confused::confused:

P.S. I deleted the package then when I got this message, I re-downloaded it.

---

### Post by Crafty Kisses on 2008-04-02
> **whizkid515 said:**
> Whenever I try to load Synaptic, update manager, or try to install a package with apt-get, i get the following error message: 


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package conexant needs to be reinstalled, but I can't find an archive for it.'

Can anyone help me?:confused::confused::confused:

P.S. I deleted the package then when I got this message, I re-downloaded it.

Try doing the following in the terminal: ```
synaptic
``` What happens then?

---

### Post by whizkid515 on 2008-04-02
Same thing happens, only it gives a warning about starting without 'sudo'.

---

### Post by whizkid515 on 2008-04-05
Umm, this is really urgent, I haven't been able to update my computer in over a month, and I don't mean to be a jerk, but I need an answer ASAP!!!!!

---

### Post by warp99 on 2008-04-05
Edit: 

I didn't notice that you tried to update with apt-get, my mistake. You can reinstall the dpkg package management application, which including the missing component [here]("http://packages.ubuntu.com/gutsy/dpkg"). The run the following:

```
sudo dpkg -i dpkg_1.14.5ubuntu16_i386.deb
```

---

### Post by smo0th on 2008-04-05
did you try using sudo? what else you did? what version are you using? I never had this problem before so I don't how to help you but you should be more specific, provide command line outputs, screenshots, etc.

---

### Post by whizkid515 on 2008-04-06
<snip>

I can access the internet, but update-manager won't work, and I don't know if this is linked, but GDebi won't work either. I'm kinda new to Linux, and I've been using it a lot lately because NONE of my networking works under windows (packet receiving problem, it's a windows thing lol), and I am not completely secure under Linux because I can't update!

---

### Post by bapoumba on 2008-04-06
Please post the complete error message to:
```
sudo apt-get update
```
along with your sources.list:
```
cat /etc/apt/sources.list
```

Which package did you delete, and how? I cannot find a packages labeled "conexant" in the ubuntu repositories.

---

