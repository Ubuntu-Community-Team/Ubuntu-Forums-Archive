---
title: "Unmet dependencies error. Usual solution not working."
date: 2013-09-12
forum: General Help
---

### Post by SASDOE2 on 2013-09-12
Hi all, I have been having this problem for a while now and can't seem to find a suitable solution on the world wide web. Whenever I try to upgrade my system or install a new package, apt returns this error: [http://pastebin.com/96eKZfJd](http://pastebin.com/96eKZfJd)I tried apt-get install -f but got the same error message.I have also tried manually installing the linuxserver package, but failed with the same message: [http://pastebin.com/hnemhRvg](http://pastebin.com/hnemhRvg) Any ideas why this is happening and how I could fix it? Cheers!EDIT : modified to add pastebins instead of one line CODE sets.

---

### Post by ian-weisser on 2013-09-12
Why are you trying to install an *older* version of the package?
Is something wrong with the newer version?

---

### Post by SASDOE2 on 2013-09-13
Because now whenever I try to install something, or upgrade my system, I get this error : [http://pastebin.com/96eKZfJd](http://pastebin.com/96eKZfJd) I also find it weird that I need an older version of the package, but am only following error messages.

---

### Post by varunendra on 2013-09-13
Please post the outputs of -
```
dpkg -l | egrep 'linux-image|linux-headers|linux-server'
```
So we can see which versions of these packages are installed. We may then try to purge the offending packages instead of trying to fix them.

---

### Post by SASDOE2 on 2013-09-13
[http://pastebin.com/4VRfpGpA](http://pastebin.com/4VRfpGpA)

---

### Post by varunendra on 2013-09-13
I see that you have been using the normal desktop kernel and headers. Why are you trying the server kernel now? Since 12.04, they are same (see point 3 [here]("https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F")). The different names exist just to satisfy the dependencies that existing packages may have on them.

Onto the issue-

Since you have older kernels installed, I'd suggest to boot into an older one, preferably 3.2.0-44 (since it is just one version older than the offending one), and purge the problematic package -
```
sudo apt-get purge linux-server
```

In fact, I suggest to remove the newer server image (metapackage, header, image) too, if you don't have any specific reasons to be using it.

Then do -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Hopefully, everything will go smooth this time and then you can install your desired packages.

**PS:**
You can free quite some disk space by removing the older kernels that you don't use. Generally, it is recommended to keep one or two previous, working ones, just in case.. (like this one ;))

---

### Post by SASDOE2 on 2013-09-13
I am actually running ubuntu server, so the fact i am using the normal ones surprises me !

---

### Post by varunendra on 2013-09-13
Hmm.. probably it corroborates the fact that the desktop and server images as well as headers are same now.

Whatever be the case, just run the three commands I suggested and the problem should go away.

You may try purging it from your currently running kernel as well, since it is just a metapackage.

---

### Post by SASDOE2 on 2013-09-13
That did the job, great thanks !

---

### Post by varunendra on 2013-09-13
You're welcome ! :)

---

