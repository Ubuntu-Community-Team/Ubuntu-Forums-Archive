---
title: "Error when starting a Samba4 DC server."
date: 2015-06-07
forum: General Help
---

### Post by Ruben_van_Komen on 2015-06-07
Hey,

I'm not sure if i'm posting this topic on the right section of the forum but i'm kinda new to this.

I get the following error when starting Samba and i don't know how to fix it.

```

samba version 4.0.26 started.
Copyright Andrew Tridgell and the Samba Team 1992-2012
samba: using 'standard' process model
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
Failed to listen on :::53 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
file_server smbd daemon exited normally
task_server_terminate: [smbd child process exited]
Failed to bind to :::53 TCP - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
Failed to listen on 0.0.0.0:53 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
Failed to bind to 0.0.0.0:53 TCP - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
task_server_terminate: [dns failed to setup interfaces]
samba_terminate: dns failed to setup interfaces

```

I'm also not sure what information to post further so if you need any information i will be happy to provide it.

Thanks for the help!
Ruben

---

### Post by Maimster on 2015-07-07
Ruben did you ever get this fixed?

---

