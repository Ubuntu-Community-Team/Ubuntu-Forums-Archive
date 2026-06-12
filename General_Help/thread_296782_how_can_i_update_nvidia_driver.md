---
title: "how can i update nvidia driver"
date: 2006-11-10
forum: General Help
---

### Post by kewayu on 2006-11-10
my display card is geforce4,how can i update driver with 'apt-get' command.thanks

---

### Post by funkyade on 2006-11-10
```
sudo aptitude install nvidia-kernel-1.0.8776
```

personally use the nvidia drivers from nvidia's site - you get the latest versions that way.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

you need to make the downloaded file executable 'chmod +x <filename>', drop to a tty by doing ALT+CTRL+F1, login, and cd to whereever you downloaded the file then run it as root by doing 'sudo ./<filename>'. then follow the prompts but don't let it find a kernel module let it build it's own. It will update xorg.conf and remove older drivers automatically.

hth

---

### Post by kewayu on 2006-11-10
Thank you,Funkyade
I also found the way with 'apt-get' command   
   sudo apt-get install nvidia-glx
   sudo nvidia-xconfig

---

