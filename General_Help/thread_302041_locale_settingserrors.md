---
title: "locale settings/errors"
date: 2006-11-18
forum: General Help
---

### Post by Brando569 on 2006-11-18
whenever i try to compile a kernel in edgy i get this error/warning, its not really effecting anything its just annoying and clogs up the terminal window. how can i fix this?

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)

```

---

### Post by ebash on 2006-11-18
Modify your environment and set the variable LC_ALL and LANGUAGE. Normally these variables should already be set, but it seems that your profile is missing them.

In a shell do:
```
export LC_ALL=en_US.UTF-8 LANGUAGE=en_US.UTF-8
```

You may want to add this variables to your ~/.bashrc.

---

