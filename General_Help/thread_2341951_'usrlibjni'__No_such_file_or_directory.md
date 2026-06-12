---
title: "'/usr/lib/jni' : No such file or directory"
date: 2016-11-02
forum: General Help
---

### Post by cduchat on 2016-11-02
Hello,

I am trying to install HELYX-OS on Ubuntu 16.04 64bit according to this method: [https://openfoamwiki.net/index.php/Installation/Helyx-OS/Ubuntu](https://openfoamwiki.net/index.php/Installation/Helyx-OS/Ubuntu)
When running ```
cp -a /usr/lib/jni/libvtk* ext/
```
I get ```
cp: cannot stat '/usr/lib/jni/libvtk*': No such file or directory

```
And in fact the entire /usr/lib/jni folder is absent, while the required packages vtk6 and libvtk6-java are correctly installed... what am I missing?

Thanks,
cduchat

---

