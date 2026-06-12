---
title: "low latency kernel vs generic kernel"
date: 2007-06-02
forum: General Help
---

### Post by ZeldaFan on 2007-06-02
I installed ubuntu studio recently, and it uses a low latency kernel. What is the difference between a low latency kernel and a generic kernel, in terms of performance and other factors.

---

### Post by dave-5B on 2007-06-03
this article might have the answer

[http://digg.com/linux_unix/Low_latency_kernel_coming_in_Ubuntu_Feisty](http://digg.com/linux_unix/Low_latency_kernel_coming_in_Ubuntu_Feisty)

a short answer would be something along the lines of:
applications that run in real time and need to be responsive (like any user interface applications) are helped by a low latency kernel, but this slows down the overall throughput of the system because the processor is constantly swiching between different processes (which has a major performance penalty)

---

