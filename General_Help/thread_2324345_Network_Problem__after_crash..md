---
title: "Network Problem  after crash."
date: 2016-05-13
forum: General Help
---

### Post by georgesgiralt on 2016-05-13
Hello,
The laptop is running 14.04 LTS with up to date software. I have a problem with the i915 integrated card, the NVidia card and Bumblebee. So sometimes the display blacks out when switching from one user (me) to another (my wife). 
Last time I switched, the only action left was to cut the power to the laptop and restart. 
Upon restart, I've no network and networkManager refuses to start even in no-daemon mode.  Here are the errors  it gave :
```

root@espineux:/etc/NetworkManager# NetworkManager --no-daemon

(NetworkManager:4080): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file does not have group 'connectivity'
NetworkManager[4080]: <info> NetworkManager (version 0.9.8.8) is starting...
NetworkManager[4080]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
NetworkManager[4080]: <info> WEXT support is enabled
Segmentation fault (core dumped)
root@espineux:/etc/NetworkManager# 

```
I've searched all I could and all logs and found nothing. Google does not give much So I ask here for help. 
Many thanks in advance for your help.

---

