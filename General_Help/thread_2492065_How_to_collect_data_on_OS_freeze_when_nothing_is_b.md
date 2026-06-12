---
title: "How to collect data on OS freeze when nothing is being written to system logs?"
date: 2023-10-29
forum: General Help
---

### Post by Doug0915 on 2023-10-29
Here is my attempt to improve the grammar and clarity of the post:

I have a rather perplexing problem. 

I can reliably reproduce a system-wide freeze whenever Firefox has hardware acceleration enabled and a specific YouTube video is played. When I turn off hardware acceleration, the issue does not occur.

After the OS freezes (unrecoverable, no virtual consoles available), Xorg or Wayland becomes completely unresponsive and I cannot SSH into the system. 

There are no relevant error messages in the kernel log or syslog.

What should I do next to collect more debugging information? Are there additional logging or debugging options I could enable?

It seems there are two distinct issues here:

1. The initial trigger appears to be Firefox with hardware acceleration enabled playing a specific video.

2. However, whatever Firefox is doing should not be able to completely hang the kernel and prevent SSH access. 

I would like to collect more detailed logging so that developers have additional data to help investigate the root causes.

Any assistance is appreciated! Any suggestions or maybe I should post in another sub-forum?

thanks

---

### Post by dragonfly41 on 2023-10-29
In past freeze case I did find that Firefox extensions were the cause and/or too many tabs open.

You might test this *theory* by having multiple firefox profiles.

One stripped back bare bone profile with no extensions enabled and minimal open tabs to test for freezes.

If there is a particular problematic YouTube video does it work in Brave browser, for example, without freezing? Just plodding detective work.

---

### Post by MAFoElffen on 2023-10-29
To run a stack trace on Firefox, start Firefox like this:
```

snap run --strace firefox | tee ./firefox.strace

```
Ensure wherever you create that file has lots of room. That is going to generate lots of data. You will see everything that is happening to it.

---

