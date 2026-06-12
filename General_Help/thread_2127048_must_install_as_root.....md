---
title: "must install as root....?"
date: 2013-03-18
forum: General Help
---

### Post by goldbeard on 2013-03-18
Hello,

I am trying to get Ubuntu to play nice with the new Geforce GTX 690 graphics card.

If there is another post for this, please just put it up. I know your time is valuable. I just didn't find one that fit for me.

Here is a link to the 64 bit driver [http://www.nvidia.in/object/linux-display-amd64-295.49-driver-in.html](http://www.nvidia.in/object/linux-display-amd64-295.49-driver-in.html)


Here is a copy of what I put in my terminal....


kiteboat@kiteboat-System-Product-Name:~/Desktop$ ./NVIDIA-Linux-x86_64-295.49.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 295.49.........................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.

Then it tells me Error: Must be installed as root

I don't know what I am doing enough to play with root by myself.

What do I do?

---

### Post by lisati on 2013-03-18
The method of *temporarily* gaining "root" access generally recommended here on the forum is through the "sudo" command, as described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have any questions, feel free to ask.

---

### Post by goldbeard on 2013-03-18
Thanks lisati

I tried everything again and typed in "sudo" before it. Now I got the following....

ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by whatthefunk on 2013-03-19
You need to kill x server first.  
[http://askubuntu.com/questions/131051/how-to-kill-and-to-start-the-x-server](http://askubuntu.com/questions/131051/how-to-kill-and-to-start-the-x-server)

This will drop you into a command line where you can then install your new driver.

---

### Post by ManamiVixen on 2013-03-19
Wait, you need a more up to date driver. 295 is too old. Use 310 series instead.

---

### Post by goldbeard on 2013-03-19
Right. I am trying to kill x server. For some reason it is not regocinizing my username and password and I can't log in. I am putting in the same username and pword I used when I installed Ubuntu. 
Am I missing something? I am using the same username and password that I log into the computer when I start it up?

---

### Post by solarghost on 2013-03-19
Should be yes, I would suggest that you go to a terminal while you are still in your normal session and type:

```
whoami
```

just to make sure you have the right username.

---

### Post by goldbeard on 2013-03-20
thank you all. I fixed it. I just reformated my hard drives, started clean and installed the latest and greatest versions of everything needed. I'm good. Except now the sound doesn't work.......   :)

---

