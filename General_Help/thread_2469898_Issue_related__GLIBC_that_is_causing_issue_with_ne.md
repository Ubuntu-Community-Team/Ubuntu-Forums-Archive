---
title: "Issue related  GLIBC that is causing issue with neovim"
date: 2021-12-13
forum: General Help
---

### Post by rpra006 on 2021-12-13
Hi there,
I have searched all over to fix the following issue but I cannot fix this issue on my desktop.
Following GLIBC message is causing my neovim not to work properly. 

How do I fix this GLIBC error please.

Please help me fix this error. I have come to a complete road block. 

Following error message from the log file based on running :checkhealth within neovim. 

```

## The following errors have been detected:   - ERROR: python(highlights): Failed to load parser: uv_dlopen: /snap/core18/current/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libstdc++.so.6)   - ERROR: python(locals): Failed to load parser: uv_dlopen: /snap/core18/current/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libstdc++.so.6)   - ERROR: python(folds): Failed to load parser: uv_dlopen: /snap/core18/current/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libstdc++.so.6)   - ERROR: python(indents): Failed to load parser: uv_dlopen: /snap/core18/current/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libstdc++.so.6)   - ERROR: python(injections): Failed to load parser: uv_dlopen: /snap/core18/current/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /lib/x86_64-linux-gnu/libstdc++.so.6)  

```

I am following version:
[FONT=monospace][COLOR=#000000]Distributor ID: Ubuntu [/COLOR]
Description:    Ubuntu 21.10 
Release:        21.10 
Codename:       impish

[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]ldd --version [/COLOR]
ldd (Ubuntu GLIBC 2.34-0ubuntu3) 2.34 
Copyright (C) 2021 Free Software Foundation, Inc. 
This is free software; see the source for copying conditions.  There is NO 
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 
Written by Roland McGrath and Ulrich Drepper.


[/FONT]



[/FONT]

---

