---
title: "Must install program as root - Install failing due to X Window"
date: 2018-03-26
forum: General Help
---

### Post by backspin on 2018-03-26
I need to install a program as root, but it's failing due to an error (Graphics Environment).

When I try to start xclock as root, I get the following error:   **Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0**

I've tried exporting .Xauthority like so but I continue to get the same error...   export XAUTHORITY=/home/backspin/.Xauthority

Just to be clear, I'm not ssh, but local to the machine and just switching to root from user like so...  sudo su -   OR  su -

So, what am I missing here to be able to install this program as root?

Thanks.

---

### Post by backspin on 2018-03-26
ah... nevermind, I think I got it.

xhost +local:

---

