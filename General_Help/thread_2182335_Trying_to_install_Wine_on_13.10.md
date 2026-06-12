---
title: "Trying to install Wine on 13.10"
date: 2013-10-20
forum: General Help
---

### Post by nXnMbpT on 2013-10-20
I am trying to install Wine and am getting this after 'winecfg'...

```
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000d), starting debugger...
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0012), starting debugger...
wine client error:15: write: Bad file descriptor
wine client error:12: write: Bad file descriptor
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073740972
wine client error:10: write: Bad file descriptor
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: cannot open shared object file: No such file or directory
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 001b), starting debugger...
wine client error:1e: write: Bad file descriptor
wine client error:1b: write: Bad file descriptor

```

Also get a couple of 'Program Error' windows...

---

### Post by nXnMbpT on 2013-10-20
I keep getting an error when trying to run 'winecfg' on 13.10

```
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000d), starting debugger...
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0012), starting debugger...
wine client error:15: write: Bad file descriptor
wine client error:12: write: Bad file descriptor
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073740972
wine client error:10: write: Bad file descriptor
p11-kit: couldn't load module:  /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so:  /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: cannot open shared  object file: No such file or directory
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 001b), starting debugger...
wine client error:1e: write: Bad file descriptor
wine client error:1b: write: Bad file descriptor

```

Also get a couple of 'Program Error' windows...

---

### Post by Toz on 2013-10-21
*Moved duplicate post to this thread*

How did you install wine? Through the software centre?

What command are you using or how are you running winecfg?

Have you ever run wine as root using sudo? What does the following command return?
```
ls -lR ~/.wine | grep root
```

Is your hard drive full?
```
df -h
```

---

### Post by nXnMbpT on 2013-10-21
Sorry for double post...

I was following a tutorial on how to get wine set up and for some reason the commands were not working, so I downgraded back to 13.04 and tried it again and was able to get it with no issues at all. I no longer need help with this issue. Thanks.

---

