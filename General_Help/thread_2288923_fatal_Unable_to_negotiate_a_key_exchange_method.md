---
title: "fatal: Unable to negotiate a key exchange method"
date: 2015-07-30
forum: General Help
---

### Post by cncr04s on 2015-07-30
Hi, I recently installed ubuntu server 15.04 x64 onto a local vmware vm.
I have console access, however I want to be able to ssh into it with my normal software that I use,and use remotely.
I keep having an issue with getting the openssh server to work.

I originally had errors relating to invalid key methods on the server, i changed them to match what my client supports, but it only got me to the next error.
I'm not sure what else to do, does any have have any idea?

I'm unable to get text input so I'll try some images with with the error messages>
[IMG]http://www.afxr.net/a9c8d3d04d9e245ff0bcbfc395057092.png[/IMG]
[IMG]http://www.afxr.net/bec078a81bf7591cd0d6d54816490c15.png[/IMG]

---

### Post by cncr04s on 2015-07-30
Well, I was hoping some one knew the answer.

I did figure this out. 
[http://sourceforge.net/p/jsch/bugs/79/](http://sourceforge.net/p/jsch/bugs/79/) 
Pointed me in the right direction, this version of openssh is missing diffie-hellman-group1-sha1 in the KexAlgorithims default list. it's there in the log, though is difficult to interpolate that its from the client and that the server doesn't have it enabled.

---

