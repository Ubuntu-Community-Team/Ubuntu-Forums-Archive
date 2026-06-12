---
title: "Why can't I install libsdl1.2-dev?"
date: 2006-08-29
forum: General Help
---

### Post by Hyperonic on 2006-08-29
I need libsdl1.2-dev to compile a program I downloaded. The following occurs as I attempt to download and install libsdl1.2-dev...

```
kenny@FOX:~/zsnes_1_42/src$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
```

So, okay, I should just add libartsc0-dev to the command and it should work? No, it depended on another package. I add that package, and I get the same results until this...

```
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
E: Broken packages
```

I type "sudo apt-get install libglib2.0" and it says that "libglib2.0-0 is already the newest version."

The Package Manager found under System > Administration gives me simliar results.

:confused:

---

