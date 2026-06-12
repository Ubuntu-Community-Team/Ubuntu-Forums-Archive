---
title: "System is crashing upon ldconfig"
date: 2020-05-21
forum: General Help
---

### Post by vijay26 on 2020-05-21
Hi Team,

I'm bit new to the dynamic linking. 
Here is steps.
I've my application which is having inbuild libs in a location and it also has few system libs which my application are refferring (say ld-linux-x86-64.so,libc.so, libdl.so, librt.so, libopencv.so etc).
I created a new config file(say app.config) in /etc/ld.so.conf.d/ and update my application lib path in that. I did ldconfig as well.
When I ran my application its working fine but other applications like doc viewer as not opening.
When I debug the case, found that libm used by other applications as referring to the my path and its crashing.
More worry is most of the time my OS is getting crashed completely after running the ldconfig.

I tried the other way as well, instead of creating the config file I updated the existing config file x86_64-linux-gnu.conf by adding my path after the system path. Even then my OS is getting crashed.
In this case, my application is referring to the system paths as it comes first in the x86_64-linux-gnu.conf.


Here are my questions,

1. Why the OS is crashing everytime?
2. What is the impact on keeping our own config file(app.config) or updating the existing system config file(x86_64-linux-gnu.conf) and running ldconfig?
3. What is the impact on keeping the system libs under my path? How to overcome this issue?
4. Is there a way where I can keep my path as application specific? where only my application will refer to that path others should not.

looking for your help.

Thanks

---

### Post by slickymaster on 2020-05-21
*Thread moved to **General Help**.*

---

