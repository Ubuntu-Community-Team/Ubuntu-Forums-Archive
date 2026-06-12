---
title: "VNC client can’t connect to Ubuntu 18.04 RD"
date: 2018-05-14
forum: General Help
---

### Post by yuri-weinstein on 2018-05-14
Enabled Remote Desktop in bionic and was able to connect with Remmina, nice :)

but VNC client (actually two clients I tried) won’t cinnect from either windows nor from iPhone/iPad 

any clues what’s going on?

gbx

---

### Post by nlee2 on 2018-05-14
I can connect to vino-server without any problems. How did you enable remote desktop, which 2 vnc clients are not connecting, where are the logs?

---

### Post by yuri-weinstein on 2018-05-15
> **nlee2 said:**
> I can connect to vino-server without any problems. How did you enable remote desktop, which 2 vnc clients are not connecting, where are the logs?

@nlee2 thx for reply.

I just enabled Screen Sharing in bionic.
And I can't connect from Windows or iOS with VNC client.
Error "the authentication mechanism requested cannot be provided"

I understand that I can install x11vnc or similar and it will work, but the question is why can't it as is?

---

### Post by nlee2 on 2018-05-15
A solution is disabling the encryption completely, by

gsettings set org.gnome.Vino require-encryption false

---

### Post by yuri-weinstein on 2018-05-15
Thank you, kind sir, it worked !

I suspected this is about encryption but had no clue :)

---

