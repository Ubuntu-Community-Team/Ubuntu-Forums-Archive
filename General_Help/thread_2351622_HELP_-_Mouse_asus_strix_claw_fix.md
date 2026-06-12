---
title: "HELP - Mouse asus strix claw fix"
date: 2017-02-05
forum: General Help
---

### Post by silva-filipe11 on 2017-02-05
Heloo there.


My mouse "asus strix claw" freezes whenever I press the additional buttons, like the dpi ones. I found a fix: https://github.com/hamer/strix-claw" but when i try to run "make" i get :


```
gcc -std=gnu99 -W -Wall -Werror -lusb-1.0  strix-claw.o -o strix-claw
strix-claw.o: In function `main':
strix-claw.c:(.text+0x9b): undefined reference to `libusb_init'
strix-claw.c:(.text+0xb4): undefined reference to `libusb_get_device_list'
strix-claw.c:(.text+0xd6): undefined reference to `libusb_open_device_with_vid_pid'
strix-claw.c:(.text+0xff): undefined reference to `libusb_detach_kernel_driver'
strix-claw.c:(.text+0x113): undefined reference to `libusb_claim_interface'
strix-claw.c:(.text+0x125): undefined reference to `libusb_alloc_transfer'
strix-claw.c:(.text+0x1f3): undefined reference to `libusb_submit_transfer'
strix-claw.c:(.text+0x212): undefined reference to `libusb_cancel_transfer'
strix-claw.c:(.text+0x22b): undefined reference to `libusb_handle_events_completed'
strix-claw.c:(.text+0x251): undefined reference to `libusb_free_transfer'
strix-claw.c:(.text+0x263): undefined reference to `libusb_close'
strix-claw.c:(.text+0x27a): undefined reference to `libusb_free_device_list'
strix-claw.c:(.text+0x28c): undefined reference to `libusb_exit'
collect2: error: ld returned 1 exit status
Makefile:17: recipe for target 'strix-claw' failed
make: *** [strix-claw] Error 1
```


I tried to find the solution online, but I was not able to fix it, maybie because I'm a noob.
I would appreciate very much any insight on the problem :)

---

