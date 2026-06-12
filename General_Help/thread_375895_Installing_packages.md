---
title: "Installing packages"
date: 2007-03-04
forum: General Help
---

### Post by amphet on 2007-03-04
Everytime I download a package this error would follow:

```

dpkg: serious warning: files list file for package `module-assistant' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dh-make' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.17-10-386' missing, assuming package has no files currently installed.

```

packages install fine, but I dont like that "serious warning".

---

### Post by Ramses de Norre on 2007-03-04
What's the output of this:```
sudo aptitude reinstall module-assistant dh-make linux-headers-2.6.17-10-386
```

---

### Post by amphet on 2007-03-04
that fixed it, thanks.

---

