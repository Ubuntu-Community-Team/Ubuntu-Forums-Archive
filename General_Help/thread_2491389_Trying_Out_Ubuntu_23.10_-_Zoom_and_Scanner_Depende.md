---
title: "Trying Out Ubuntu 23.10 - Zoom and Scanner Dependency Issues"
date: 2023-10-06
forum: General Help
---

### Post by iamjiwjr on 2023-10-06
Right or wrong, I still find the Zoom snap impractical since I can't get it to accept virtual backgrounds. So I went to the deb alternative from the Zoom.us site. This package has installed many times successfully in previous releases - and I still think this deb is the best all around Zoom experience available for Linux. I was met by the dependency monster when I attempted to install it:

The following packages have unmet dependencies:
 zoom : Depends: libgl1-mesa-glx but it is not installable
        Depends: libegl1-mesa but it is not installable
        
Likewise when I tried to install brscan-skey deb, as I have done in the past on previous releases a lot of times, I get another dependency bonk:


The following packages have unmet dependencies:
 brscan-skey : Depends: libsane (>= 1.0.11-3) but it is not installable

Just a heads up. And if there are any suggestions I welcome them.

---

### Post by ActionParsnip on 2023-10-06
[https://askubuntu.com/questions/1348744/cannot-install-zoom-or-webex-meetings-unsatisfiable-dependency-libgl1-mesa-glx](https://askubuntu.com/questions/1348744/cannot-install-zoom-or-webex-meetings-unsatisfiable-dependency-libgl1-mesa-glx)
A fix here

---

### Post by MAFoElffen on 2023-10-06
That AskUbuntu Question was for 21.04 (before Jammy). He is on Mantic, which is not released yet. I'm still testing the heck out of Mantic and digging up more things for them to fix every day.

23.10 is still beta in the Dev Cycle... It's due to release on the 20th. The repo's are still not locked in yet for the final. The repo lock should be next week some time.

I'm always surprised by a few unexpected things when they gift-wrap all the pieces together into the Release ISO. They do not always match the test pieces we are testing in the dailies. It seems to work out. LOL

---

### Post by acheronuk on 2023-10-13
The uninstallable packages are dummy transitional ones that have now been dropped. The makers of the debs you are trying to install need to fix them to depend on the current real packages.

---

