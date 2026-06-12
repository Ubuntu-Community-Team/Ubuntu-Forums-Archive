---
title: "Ubuntu Random Crashes"
date: 2019-10-02
forum: General Help
---

### Post by jaimeamonc on 2019-10-02
I've been experiencing random crashes constantly since I've switched to Ubuntu.

I first start on Ubuntu 19 but thought I'd have less on 18 but it is still occurring, albeit less frequently.

I'm normally just using chrome but sometimes I'm doing web development and running a development server. 

I'm including the syslog, any help would be appreciated! Let me know if there's anything else I can provide.

System:
Huawei Matebook D Ryzen

Syslog:
[https://drive.google.com/file/d/1QdRfPqpR96VnWinHNM6z-x9jlUouwIz2/view?usp=sharing](https://drive.google.com/file/d/1QdRfPqpR96VnWinHNM6z-x9jlUouwIz2/view?usp=sharing)

---

### Post by jaimeamonc on 2019-10-02
I see the last thing before the crash is:
google-chrome.desktop[2322]: [2357:2357:1002/183717.427224:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
\00\00\00\00\00\00\00\00\

I've seen various suggestions online to disable hardware acceleration on chrome. Any thoughts?

---

