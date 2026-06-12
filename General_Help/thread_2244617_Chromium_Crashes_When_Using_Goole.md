---
title: "Chromium Crashes When Using Goole"
date: 2014-09-17
forum: General Help
---

### Post by Myst1234 on 2014-09-17
Hey everyone,

I have what seems to be a "unique" issue. I just got a new Lenovo ThinkPad, upgraded RAM and looking into upgrading to 256 SSD! This machine is amazing. Ok enough techie nerd talk, onto the problem.

I've just installed Ubuntu 14.04 on this awesome Linux machine, and then installed Chromium (my personal browser of choice.) but when I try to search ANYTHING on Google, it crashes.

I've seen other issues with Chromium GPU, and Chromium crashing the entire system, but neither of these things are happening with me. The system is fine, everything works properly, but trying to search crashes and closes Chromium. 

I can go straight to a URL with no problems so far, but searching crashes it. I know, very odd.

Any and all help would be greatly appreciated and thanks in advance for your assistance.

---

### Post by tgalati4 on 2014-09-17
Try installing *google-chrome* and see if it works properly.  The html5 engine has hardware video rendering and that may not be working (or not included) in chromium.

What graphics card?

```
lspci
```

Run chromium in a terminal (with perhaps the -debug switch) and see what errors pop up.  Even post them.

---

### Post by Myst1234 on 2014-09-17
Radeon 

google-chrome was not found

---

### Post by Myst1234 on 2014-09-17
```
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[2684:2684:0917/152002:ERROR:sandbox_linux.cc(308)] InitializeSandbox() called with multiple threads in process gpu-process
[2647:2707:0917/152028:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
[2647:2678:0917/152104:FATAL:url_request.cc(709)] Trying to send secure referrer for insecure load
Aborted (core dumped)


```

This is what came up when I ran it through the terminal and tried searching on Google.

Again, everything works fine EXCEPT Google search. Bing and Yahoo both navigate perfectly, but as soon as I try to search using Google it crashes and closes.

---

### Post by Myst1234 on 2014-09-17
Appaently this is an "on purpose" bug. I'm just going through the process to get Chrome-Stable. Thanks everyone

---

