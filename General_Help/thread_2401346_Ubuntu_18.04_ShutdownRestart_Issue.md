---
title: "Ubuntu 18.04 Shutdown/Restart Issue"
date: 2018-09-17
forum: General Help
---

### Post by sipheren2 on 2018-09-17
Hi,


So I am a bit of a Linux noob, trying to get my head around how it all works. I have got a nice install of Ubuntu going, updated the kernel to 4.18 and using the latest Nvidia drivers.


I am not sure what thing I actually did to cause it but now when I restart or shutdown the system takes ages to complete, it’s like it’s just hanging there waiting for something.


I pressed esc and then Ctrl+Alt+F1 to bring up the console and the attached image is what I am seeing.


Does anyone know what is happening or can give me some advice on where to look for the issue?


Thanks

---

### Post by garvinrick4 on 2018-09-17
Try another kernel,when you hit your boot screen arrow down one hit enter and see if another kernel
 installed and boot with that kernel. Always keep a few kernels installed in case one doesn't work you
have another or can see if is a kernel problem. I rarely get a kernel problem at all usually when I install
one that is still in development stage.

---

### Post by lotharmat on 2018-09-20
I got this! - systemd is trying (unsuccessfully) to stop a process..

Edit the following:

 /etc/systemd/system.conf 

and  change the value in DefaultTimeoutStopSec to 4s..then save the file and restart your computer..
Now it should work.. 

(well it cured it on mine anyway)

---

