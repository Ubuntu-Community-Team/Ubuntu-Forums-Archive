---
title: "Ubuntu 23.10 lock screen issue"
date: 2024-04-03
forum: General Help
---

### Post by ayon+mukherjee on 2024-04-03
On my Ubuntu 23.10 laptop, with hardware and software as follows:

# System Details Report

## Hardware Information:
- **Hardware Model:**                              Lenovo Lenovo V330-15IKB
- **Memory:**                                      8.0 GiB
- **Processor:**                                   Intel® Core&#8482; i5-8250U × 8
- **Graphics:**                                    Intel® UHD Graphics 620 (KBL GT2)
- **Disk Capacity:**                               1.0 TB

## Software Information:
- **Firmware Version:**                            6SCN41WW
- **OS Name:**                                     Ubuntu 23.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               45.2
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.5.0-26-generic

I'm having a strange problem while using the Lock Screen function.

1. When I lock my screen and leave my computer idle, it sometimes straight-up restarts the computer.
2. When I lock my screen and leave my computer idle, it sometimes shows that the power and num-lock LED's are on; but I'm unable to wake it up from that state - so I have to use the power button to shutdown and start it again.
3. When I lock my screen and leave my computer idle, it sometimes just shuts down. This happens only when the flap/lid is closed.

Barring a few times, when I check immediately after locking the screen if everything is fine; the lock-screen shows up properly - with an option to unlock with my password. But, after a while; after the second time it goes dark; the lock-screen stops working and one of the above three scenarios occur.
Sometimes though, right after locking, the touchpad and the keyboard become non-responsive and I realise that I'm in scenario 2 mentioned above.

I have tried everything that I could find - using tweaks to ignore the lid-switch; using the settings to turn-off auto lock-screen, screen-dimming, etc.; adding MUTTER_DEBUG_KMS_THREAD_TYPE=user to my /etc/enviroment file; but absolutely nothing works! The unreliable behaviour of the lock-screen function remains.

I'm in dire need of help! I implore somebody to help! Please!

---

