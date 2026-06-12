---
title: "nvidia drivers messed up"
date: 2008-01-29
forum: General Help
---

### Post by chris23 on 2008-01-29
Hello, 
I've got an nvidia 6600gt gpu and with a fresh install and after enabling the restricted drivers all worked flawlessly. My resolution ( 1680x1050 ) was detected and everything was ok.

After trying to install the nvidia drivers ( from the official web site) don't ask why...
it all got messed up! i can't get my resolution and bla bla bla ...i tried reconfiguring the x-server, installing the drivers again but I didn't manage to get it done.

Is there a way to uninstall everything and get a clean install of nvidia drivers detect my resolution automatically as the first time...

I am totally noob as you might understand..and sorry for the long post.

thank you.

---

### Post by jazzgossen on 2008-01-29
Normally, you shouldn't need to install the drivers from the web site. Try installing the nvidia-glx-new package (with apt-get or synaptic) and see if that helps.

---

### Post by PmDematagoda on 2008-01-29
For me it seems that installing the driver directly from the Nvidia website is more reliable than installing it using the Restricted Drivers Manager, especially for new VGA cards such as the 8800GT.

But for your VGA card, installing the Nvidia driver by the method suggested by jazzgossen should be enough. Also, when installing the Nvidia driver this way, you would need to enable it using:-
```
sudo nvidia-settings --config enable
```
and then reconfiguring your X-Server.

---

