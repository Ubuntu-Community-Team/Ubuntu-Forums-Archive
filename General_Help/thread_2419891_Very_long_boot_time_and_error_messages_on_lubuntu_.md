---
title: "Very long boot time and error messages on lubuntu 19.04"
date: 2019-05-26
forum: General Help
---

### Post by obywatel on 2019-05-26
Hi,

I just installed Lubuntu 19.04 64 bit on Dell inspiron 1525(old laptop from 2008 intel Pentium T2370/Mobile Intel GM965 Express  ) upgraded with ssd 120Gb and 4Gb of ram, but I'm having problem with very long boot times (over a minute) with error messages. 

```
[drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [CRTC:41:pipe B] flip_done timed out
[drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:35:plane B] flip_done timed out
[drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CONNECTOR:50:SVIDEO-1] flip_done timed out

```
I have already found a part of the solution by modify grub with the line[I]
 ```
GRUB_CMDLINE_LINUX_DEFAULT="**video=SVIDEO-1:d** quiet splash".
```
This helps only with the error message: 
[/I]```
[drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CONNECTOR:50:SVIDEO-1] flip_done timed out
```
and it speeds up a boot time only a little bit. 

The other two error messages still show up: 
```
[drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [CRTC:41:pipe B] flip_done timed out
[drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:35:plane B] flip_done timed out

```

There is also delay on  the shut down. Those error  messages  show up too.

any help with this issue?

---

### Post by TheFu on 2019-05-27
There are a few other threads here where we helped others use the built-in tools to determine what is impacting boot times.  Search for **systemd-analyze** commands in these forums with different options.
Here is one: [https://ubuntuforums.org/showthread.php?t=2417453&highlight=systemd-analyze+blame](https://ubuntuforums.org/showthread.php?t=2417453&highlight=systemd-analyze+blame)

19.04 isn't an LTS release, so I don't have any experience with it. Sorry.

---

