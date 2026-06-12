---
title: "Error with X"
date: 2007-07-29
forum: General Help
---

### Post by HonyTawk on 2007-07-29
To start off with im relativly new to ubuntu and linux so if you offer me help, go easy.
I installed the nvidia-glx-legacy, done the sudo command to enable it restarted and it came up a X error or something like that.
It starts to load GRUB then cuts to text based stuff.
At least, if you can, tell me what to type to go back to what i had.

---

### Post by ddrichardson on 2007-07-29
What is the error?

---

### Post by HonyTawk on 2007-07-30
When i boot up it comes up Faired to start X (graphical boot interface) then it has a yes or no bit at the bottom, sorry but i can't remember what the question for it was.

---

### Post by ddrichardson on 2007-07-30
What was the sudo command?

---

### Post by HonyTawk on 2007-07-30
It was the one to enable the nvidia-glx-legacy thing
sudo nvidia-glx-config enable

---

### Post by ddrichardson on 2007-07-30
Is the module inserted: check with modprobe. If you look at /etc/X11/xorg.conf, is the server name nvidia or nv?

---

