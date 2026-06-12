---
title: "Audacity Installation Failure"
date: 2016-05-27
forum: General Help
---

### Post by m.kools on 2016-05-27
I was trying to install audacity, I am on ubuntu xenial xerus (actually the xubuntu flavor) and ran ```
sudo apt-get install audacity
``` to install audacity. However, when I tried to run audacity I received the following error: ```
audacity: error while loading shared libraries: libid3tag.so.0: cannot open shared object file: No such file or directory
```

I do not know how to fix this. Could someone detail the steps required to debug or fix this? Interestingly, I had these problems, though later fixed, with blender (there was an error about a failure to load needed libraries).

I found this thread [https://sourceforge.net/p/audacity/mailman/message/12268693/](https://sourceforge.net/p/audacity/mailman/message/12268693/) where a similar problem was discussed but I was unsure on how to use the suggested solution or if it would work for me.

---

### Post by Linuxisfast on 2016-05-28
Can you try it again after installing ubuntu-restricted-extras and libavcodec-extra

---

### Post by RobGoss on 2016-05-28
> **m.kools said:**
> I was trying to install audacity, I am on ubuntu xenial xerus (actually the xubuntu flavor) and ran ```
sudo apt-get install audacity
``` to install audacity. However, when I tried to run audacity I received the following error: ```
audacity: error while loading shared libraries: libid3tag.so.0: cannot open shared object file: No such file or directory
```

I do not know how to fix this. Could someone detail the steps required to debug or fix this? Interestingly, I had these problems, though later fixed, with blender (there was an error about a failure to load needed libraries).

I found this thread [https://sourceforge.net/p/audacity/mailman/message/12268693/](https://sourceforge.net/p/audacity/mailman/message/12268693/) where a similar problem was discussed but I was unsure on how to use the suggested solution or if it would work for me.


Have you try installing Audacity using the Ubuntu software Center?

---

### Post by m.kools on 2016-05-28
@linuxisfast Sadly that did not work for me. I got the same error.

@robgoss That did not work either.

---

### Post by RobGoss on 2016-05-28
> **m.kools said:**
> @linuxisfast Sadly that did not work for me. I got the same error.

@robgoss That did not work either.

You are using Ubuntu 16.04 correct? and if so are you using the new **Ubuntu Software** to install Audacity? I just installed it with out any problem are you getting a error message of some sort?

---

### Post by deadflowr on 2016-05-28
Try reinstalling the libid3tag0 package:
```
sudo apt-get install --reinstall libid3tag0
```

Note that apt never installs anything in /usr/local, but will install in this particular library in /usr/lib.
(/usr/lib/libid3tag.so.0 is actually just a link, in 16.04, a link to /usr/lib/libid3tag.so.0.3.0, ftr)

---

### Post by m.kools on 2016-05-29
@deadflowr that worked for me, thank you.

---

