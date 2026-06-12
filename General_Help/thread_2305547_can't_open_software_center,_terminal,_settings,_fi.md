---
title: "can't open software center, terminal, settings, files ... please Help!"
date: 2015-12-06
forum: General Help
---

### Post by majid11 on 2015-12-06
Hi,

I have just installed ubuntu 14.04 LTS. then installed Anaconda, cuda7.5 and opencv and Caffe framework.
then installed textlive. everything was good but after a few minutes. I am not able to open terminals by ctrl tab t even by clicking on the icon of terminal after searching that. I am not able to open settings and software-center by clicking on them. by calling them in Xterm teminal I am receving this error:

/usr/bin/python: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgdk-3.so.0: undefined symbol: cairo_surface_set_device_scale

I really don't know what to do. last time I installed this software this happened and when I restarted I saw only a black screen with a blinking cursor. I couldn't even go to tty1. I tried a lot and searched but no luck. so I had to install ubuntu again. and this happened again. I am afraid of restarting. Please HELP me!!!

---

### Post by Bucky Ball on 2015-12-06
Welcome. Well, as you've replicated the exact same problem by using the exact same procedure as last time you might think about a bug report ...

In the meantime, you could try rebooting the machine, boot to the recovery option, drop to a root terminal and try removing what you've installed.

If that gets you back up, this time, install whatever you installed one by one and test after each to see where it falls over. Then you'll have more info for the report, if you make one, and more information to give us.

As you've installed a raft of things after OS install it is very hard to know which caused your current issue.

(If the same thing happened on a fresh install last time it was unlikely anything would be different second time around. :))

---

### Post by majid11 on 2015-12-06
thanks for your response. Last time, I thought the problem was installing ocl-icd-libopencl1 in installing opencv in 64 bit system which caused the problem and I should install nvidia-opencl. but it turned out that this was not the reason. last time I went in root terminal in recovery option. and tried to solve the problem but no luck after one day trying. after installing Anaconda, CUDA and nvidia I rebooted the system. so I am sure this is not the problem, but installing opencv and caffe are really painful. and takes long. 

Isn't there any way to solve this problem without rebooting?
I still have access to chromium browser to type this problem, Xterm Terminal, and directories.

---

### Post by Bucky Ball on 2015-12-06
In that case, uninstall opencv and caffe and see if the problem goes away. If so, add one and test it. You'll soon discover what's making it crash.

> sudo apt-get remove opencv

... etc ...

---

### Post by majid11 on 2015-12-07
I solved this problem. thanks.

during the Caffe installation due to the error of libopenblas.so : undefined reference to _gfortran... I had to define a fooLibrary.conf with the address of Anaconda's lib in etc/ls.so.conf.d. this cause the Caffe to be installed, but now I noticed all of the problems afterwards caused by this file. So I had to remove it after Caffe installation which I did and Now I have terminal and other things back.

best

---

### Post by Bucky Ball on 2015-12-07
Good news and thanks for sharing the fix. :)

Please see first link in my signature to further help others.

---

### Post by adam71h on 2016-08-31
I'm having the same problem. I have tried the "[COLOR=#000000]*sudo apt-get remove opencv" and I still can't able to access the software centre*[/COLOR]

---

### Post by oldos2er on 2016-08-31
Hi adam71h, please start a new thread for your question; this one's getting a bit long in the tooth.

Old thread closed.

---

