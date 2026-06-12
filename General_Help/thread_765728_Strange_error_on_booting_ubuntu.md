---
title: "Strange error on booting ubuntu"
date: 2008-04-24
forum: General Help
---

### Post by xtyp on 2008-04-24
I don't know how it happens, it really confusing me. First, I install wubi 8.04 with the last iso of amd64, when it finishes I reboot and I select ubuntu on so menu. It installs perfectly. Now, I reboot and I select winxp, it boots OK, but when I boot ubuntu again after booting winxp it gives me this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help'  for a list of built-in commands.

(initramfs)


And there's no way...

---

### Post by ago on 2008-04-24
after selecting Ubuntu press esc and select either verbose mode or rescue mode

---

### Post by xtyp on 2008-04-25
No way dude, I've taked a photo, may this can help...

btw I installed wubi in my slave hdd, but i think this is not the problem, anyway... watch this

---

### Post by rekkel on 2008-04-25
> **xtyp said:**
> No way dude, I've taked a photo, may this can help...

btw I installed wubi in my slave hdd, but i think this is not the problem, anyway... watch this

Hello, 

I have the same problem

Please can somebody help.

Greetz Rick

---

### Post by ago on 2008-04-25
Try to run chkdsk /r from windows, then boot and shutdown into windows for a couple of times, then try selecting ubuntu agin

---

### Post by rekkel on 2008-04-25
I stopped windows vista when it was booting. 
ubuntu thinks that the ntfs partitions are in use.

solution:

reboot the pc en start windows. wait untill windows is compleetly booted.

restart the pc en boot ubuntu.

Then it works fine.:)

Greetz rick

---

