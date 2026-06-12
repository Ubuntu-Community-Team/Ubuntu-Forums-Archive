---
title: "After installation of amdgpu-pro driver everything works except llvm-amdgpu-dev:i386"
date: 2021-05-05
forum: General Help
---

### Post by spectatorx on 2021-05-05
Recently i've installed ubuntu 20.04 and amdgpu-pro driver stack. After installation any time i run any installation of anything or update i see in log such error:


[qoute]
 Setting up llvm-amdgpu-dev:i386 (1:11.0-1247438) .../  update-alternatives: error: alternative path /opt/amdgpu/bin/llvm-config-11.0-64 doesn't exist/  dpkg: error processing package llvm-amdgpu-dev:i386 (--configure):/  installed llvm-amdgpu-dev:i386 package post-installation script subprocess returned error exit status 2/  Errors were encountered while processing:  llvm-amdgpu-dev:i386/  E: Sub-process /usr/bin/dpkg returned an error code (1)  [/qoute]


Everything works as good as it supposed to but this error shows up in installation log. How can i fix it? I tried apt-get install -f but didn't solve the problem, other solutions i found over internet related to that package most of the time are about issues with installation of whole amdgpu-pro driver, not just this package in particular.

---

### Post by Xian on 2021-05-05
Let's try creating what the setup process is expecting. 

```
sudo touch [COLOR=#000000]/opt/amdgpu/bin/llvm-config-11.0-64[/COLOR]
```

Then a couple of maintenance commands. 
Make a note of any error outputs that occur.

```
sudo dpkg --configure -a
sudo apt-get install -f

```

If no further issues/errors then you can optionally remove the file

```
sudo rm /opt/amdgpu/bin/llvm-config-11.0-64
```

---

### Post by spectatorx on 2021-05-05
Thank you! A gentle TOUCH fixed it.

---

