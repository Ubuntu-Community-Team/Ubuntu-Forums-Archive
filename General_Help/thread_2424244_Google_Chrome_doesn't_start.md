---
title: "Google Chrome doesn't start"
date: 2019-08-05
forum: General Help
---

### Post by claus on 2019-08-05
Hi all,

today, when trying to start Google Chrome, nothing happened. When I tried to invoke Chrome via shell, I got this:

[https://artisticdiaryhome.files.wordpress.com/2019/08/screenshot-at-2019-08-05-20-24-03.png?w=625](https://artisticdiaryhome.files.wordpress.com/2019/08/screenshot-at-2019-08-05-20-24-03.png?w=625)

What can I do in order to start Chrome successfully? I have MATE as a desktop environment.

TIA,

Claus

---

### Post by claus on 2019-08-06
After an attempt of mine to reinstall Google Chrome, I am still getting error messages:
```
claus@ubuntu:~$ google-chrome-stable

(google-chrome-stable:15253): dconf-WARNING **: 05:52:36.657: Unable to open /home/claus/.local/share/flatpak/exports/share/dconf/profile/user: Permission denied
[15253:15270:0807/055236.926562:ERROR:cache_util.cc(141)] Unable to move cache folder /home/claus/.config/google-chrome/ShaderCache/GPUCache to /home/claus/.config/google-chrome/ShaderCache/old_GPUCache_000
[15253:15270:0807/055236.926640:ERROR:disk_cache.cc(178)] Unable to create cache
[15253:15270:0807/055236.926657:ERROR:shader_disk_cache.cc(623)] Shader Cache Creation failed: -2
[15253:15253:0807/055237.170709:ERROR:process_singleton_posix.cc(433)] readlink failed: Permission denied (13)
[15253:15253:0807/055237.170747:ERROR:process_singleton_posix.cc(257)] readlink(/home/claus/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[15253:15253:0807/055237.170773:ERROR:process_singleton_posix.cc(257)] readlink(/home/claus/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[15253:15253:0807/055237.170785:ERROR:process_singleton_posix.cc(281)] Failed to create /home/claus/.config/google-chrome/SingletonLock: Permission denied (13)
[15253:15253:0807/055237.170802:ERROR:process_singleton_posix.cc(433)] readlink failed: Permission denied (13)
[15253:15253:0807/055237.170815:ERROR:process_singleton_posix.cc(257)] readlink(/home/claus/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[15253:15253:0807/055237.170860:ERROR:chrome_browser_main.cc(1441)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
[15287:15287:0807/055237.179081:ERROR:sandbox_linux.cc(369)] InitializeSandbox() called with multiple threads in process gpu-process.
[15253:15270:0807/055237.188197:ERROR:browser_process_sub_thread.cc(203)] Waited 13 ms for network service

```

---

### Post by wildmanne39 on 2019-08-06
*Thread moved to **General Help a more appropriate sub-forum**.*

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

