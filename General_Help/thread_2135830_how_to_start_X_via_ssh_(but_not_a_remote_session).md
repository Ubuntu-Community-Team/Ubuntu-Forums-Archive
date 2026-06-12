---
title: "how to start X via ssh (but not a remote session)?"
date: 2013-04-15
forum: General Help
---

### Post by mark1977 on 2013-04-15
Hi,
I have a computer at work which has a graphics card that I have written openCL code for. I would like to ssh into this computer to run my code, however, the openCL SDK's (AMD's at least) seem to require that you are running X otherwise you can't make use of the GPU hardware. Is there a way I can get X running on the remote computer, so that I can compile and run my openCL code via ssh?

Thanks

Mark

ps. I realise I could start a remote X session with vnc or something but I don't have the knowhow to do this so would prefer to stick to ssh if possible.
pps. I'm running 12.04 on both computers.

---

### Post by dcstar on 2013-04-18
```
sudo startx
```

---

