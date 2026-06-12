---
title: "Unable to connect using ssh"
date: 2018-04-02
forum: General Help
---

### Post by simo2 on 2018-04-02
I have a Raspberry Pi 3 model b, the OS is Ubuntu Mate 16, everything was working fine before.


  Today I have started the rpi, I figured out I am facing a problem  which occurs during boot time due to crash while loading kernel modules,  ssh service is enabled, but even if I type the correct credentials that  I am 100% sure are correct, now ssh says that they're incorrect, also  the service of vnc is not started.


  When I have plugged the rpi into the monitor I see a message that shows in Loop on console: 

```
"Unhandled prefetch abort: breakpoint debug exception (0x002) at   0x7447beda"


```

This is apart of syslog looks like:
```

   Mar 18 04:20:45 x systemd[1]: Received SIGRTMIN+21 from PID 206 (plymouthd).
Mar 18 04:20:45 x systemd[1]: Started Light Display Manager.
Mar 18 04:20:45 x NetworkManager[642]: <info>  [1521346845.8966] device (wlan0): supplicant interface state: ready -> inactive
Mar 18 04:20:46 x snapd[647]: sizeclass=16 NumSizeClasses=2_
Mar 18 04:20:46 x ModemManager[644]: <info>  Couldn't check support for device at '/sys/devices/platform/soc/3f980000.usb/usb1/1-1/1-1.1': not supported by any plugin
Mar 18 04:20:46 x snapd[647]: fatal error: InitSizes - bad NumSizeClasses
Mar 18 04:20:46 x snapd[647]: runtime: panic before malloc heap initialized
Mar 18 04:20:46 x snapd[647]: runtime stack:
Mar 18 04:20:46 x snapd[647]: runtime.throw(0xfeaea8, 0x1e)
Mar 18 04:20:46 x snapd[647]: #011/usr/lib/go-1.6/src/runtime/panic.go:2? +0x80 fp=0x7ea3faa0 sp=0x7ea3fa94
Mar 18 04:20:46 x snapd[647]: runtime.initSizes()
Mar 18 04:20:46 x snapd[647]: #011/usr/lib/go-1.6/src/runtime/msize.go:2<8A> +0x2fc fp=0x7ea3fac8 sp=0x7ea3faa0
Mar 18 04:20:46 x snapd[647]: runtime.mallocinit()
Mar 18 04:20:46 x snapd[647]: #011/usr/lib/go-1.6/src/runtime/malloc.go:2<F5> +0x1c fp=0x7ea3fb54 sp=0x7ea3fac8
Mar 18 04:20:46 x snapd[647]: runtime.schedinit()
Mar 18 04:20:46 x snapd[647]: #011/usr/lib/go-1.6/src/runtime/proc.go:2<CD> +0x5c fp=0x7ea3fb78 sp=0x7ea3fb54
Mar 18 04:20:46 x snapd[647]: runtime.rt0_go(0x7ea3fd14, 0x76f33000, 0x7ea3fd14, 0x1, 0x6fe718, 0x76fb8000, 0xaaaaaaab, 0xc4b6dc5b, 0xccf33fe6, 0x12c, ...)
Mar 18 04:20:46 x snapd[647]: #011/usr/lib/go-1.6/src/runtime/asm_arm.s:2Y +0x8c fp=0x7ea3fbb8 sp=0x7ea3fb78
Mar 18 04:20:46 x systemd[1]: snapd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Mar 18 04:20:46 x systemd[1]: Failed to start Snappy daemon.
Mar 18 04:20:46 x systemd[1]: snapd.service: Unit entered failed state.
Mar 18 04:20:46 x systemd[1]: snapd.service: Failed with result 'exit-code'.
Mar 18 04:20:47 x kernel: [   38.566328] Unhandled prefetch abort: breakpoint debug exception (0x002) at 0x7441ceda
Mar 18 04:20:47 x systemd[1]: snapd.service: Service hold-off time over, scheduling restart.
Mar 18 04:20:47 x systemd[1]: Stopped Snappy daemon.
Mar 18 04:20:47 x systemd[1]: Starting Snappy daemon...
Mar 18 04:20:50 x snapd[835]: sizeclass=16 NumSizeClasses=2_
Mar 18 04:20:50 x snapd[835]: fatal error: InitSizes - bad NumSizeClasses
Mar 18 04:20:50 x snapd[835]: runtime: panic before malloc heap initialized
Mar 18 04:20:50 x snapd[835]: runtime stack:
Mar 18 04:20:50 x snapd[835]: runtime.throw(0x1026ea8, 0x1e)
Mar 18 04:20:50 x snapd[835]: #011/usr/lib/go-1.6/src/runtime/panic.go:2? +0x80 fp=0x7e803aa0 sp=0x7e803a94
Mar 18 04:20:50 x snapd[835]: runtime.initSizes()
Mar 18 04:20:50 x snapd[835]: #011/usr/lib/go-1.6/src/runtime/msize.go:2<8A> +0x2fc fp=0x7e803ac8 sp=0x7e803aa0
Mar 18 04:20:50 x snapd[835]: runtime.mallocinit()
Mar 18 04:20:50 x snapd[835]: #011/usr/lib/go-1.6/src/runtime/malloc.go:2<F5> +0x1c fp=0x7e803b54 sp=0x7e803ac8
Mar 18 04:20:50 x snapd[835]: runtime.schedinit()
Mar 18 04:20:50 x snapd[835]: #011/usr/lib/go-1.6/src/runtime/proc.go:2<CD> +0x5c fp=0x7e803b78 sp=0x7e803b54
Mar 18 04:20:50 x snapd[835]: runtime.rt0_go(0x7e803d14, 0x76f1f000, 0x7e803d14, 0x1, 0x73a718, 0x76fa4000, 0xaaaaaaab, 0x3b4e3c89, 0x332adf34, 0x12c, ...)
Mar 18 04:20:50 x snapd[835]: #011/usr/lib/go-1.6/src/runtime/asm_arm.s:2Y +0x8c fp=0x7e803bb8 sp=0x7e803b78
Mar 18 04:20:50 x systemd[1]: snapd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Mar 18 04:20:50 x systemd[1]: Failed to start Snappy daemon.
Mar 18 04:20:50 x systemd[1]: snapd.service: Unit entered failed state.
Mar 18 04:20:50 x systemd[1]: snapd.service: Failed with result 'exit-code'.
Mar 18 04:20:50 x systemd[1]: snapd.service: Service hold-off time over, scheduling restart.
Mar 18 04:20:50 x systemd[1]: Stopped Snappy daemon.
Mar 18 04:20:50 x systemd[1]: Starting Snappy daemon...
Mar 18 04:20:52 x hciattach[625]: Initialization timed out.
Mar 18 04:20:52 x hciattach[625]: bcm43xx_init
Mar 18 04:20:52 x hciattach[625]: Set Controller UART speed to 921600 bit/s
Mar 18 04:20:52 x hciattach[625]: Flash firmware /lib/firmware/BCM43430A1.hcd
Mar 18 04:20:52 x systemd[1]: hciuart.service: Control process exited, code=exited status=1
Mar 18 04:20:52 x systemd[1]: Failed to start Configure Bluetooth Modems connected by UART.
Mar 18 04:20:52 x systemd[1]: hciuart.service: Unit entered failed state.
Mar 18 04:20:52 x systemd[1]: hciuart.service: Failed with result 'exit-code'.
Mar 18 04:20:53 x snapd[837]: sizeclass=16 NumSizeClasses=2_
Mar 18 04:20:53 x snapd[837]: fatal error: InitSizes - bad NumSizeClasses
Mar 18 04:20:53 x snapd[837]: runtime: panic before malloc heap initialized
Mar 18 04:20:53 x snapd[837]: runtime stack:
Mar 18 04:20:53 x snapd[837]: runtime.throw(0x1024ea8, 0x1e)
Mar 18 04:20:53 x snapd[837]: #011/usr/lib/go-1.6/src/runtime/panic.go:2? +0x80 fp=0x7eb44aa0 sp=0x7eb44a94
Mar 18 04:20:53 x snapd[837]: runtime.initSizes()
```

in  auth.log
```

    Mar 18 04:20:24 x systemd-logind[645]: New seat seat0.
Mar 18 04:20:48 x sshd[1271]: Server listening on 0.0.0.0 port 22.
Mar 18 04:20:48 x sshd[1271]: Server listening on :: port 22.
Mar 18 04:35:41 x sshd[1271]: Received SIGHUP; restarting.
Mar 18 04:35:41 x sshd[1271]: Server listening on 0.0.0.0 port 22.
Mar 18 04:35:41 x sshd[1271]: Server listening on :: port 22.
Mar 18 04:35:53 x sshd[1271]: Received SIGHUP; restarting.
Mar 18 04:35:53 x sshd[1271]: Server listening on 0.0.0.0 port 22.
Mar 18 04:35:53 x sshd[1271]: Server listening on :: port 22.
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_unix.so
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_permit.so
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_loginuid.so): /lib/security/pam_loginuid.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_loginuid.so
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_env.so): /lib/security/pam_env.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_env.so
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_umask.so): /lib/security/pam_umask.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_umask.so
Mar 18 05:01:01 x CRON[3341]: PAM unable to dlopen(pam_limits.so): /lib/security/pam_limits.so: cannot open shared object file: No such file or directory
Mar 18 05:01:01 x CRON[3341]: PAM adding faulty module: pam_limits.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_unix.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_permit.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_loginuid.so): /lib/security/pam_loginuid.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_loginuid.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_env.so): /lib/security/pam_env.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_env.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_umask.so): /lib/security/pam_umask.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_umask.so
Mar 18 05:17:01 x CRON[3905]: PAM unable to dlopen(pam_limits.so): /lib/security/pam_limits.so: cannot open shared object file: No such file or directory
Mar 18 05:17:01 x CRON[3905]: PAM adding faulty module: pam_limits.so
Mar 18 06:01:01 x CRON[5443]: PAM unable to dlopen(pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: No such file or directory
Mar 18 06:01:01 x CRON[5443]: PAM adding faulty module: pam_unix.so
Mar 18 06:01:01 x CRON[5443]: PAM unable to dlopen(pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: No such file or directory
Mar 18 06:01:01 x CRON[5443]: PAM adding faulty module: pam_permit.so
```


So as you can see snapd crashes and restarted itself causing the system be unstable.
is that the source that cause ssh connection problem ? how can i fix snapd ?

---

### Post by TheFu on 2018-04-02
Could the file system be corrupted?

---

### Post by HermanAB on 2018-04-03
Hmm, an RPi runs off a SD card.  It may have a faulty block.  You probably need to re-install on a new SD card to fix this issue.

---

### Post by simo2 on 2018-04-03
> **HermanAB said:**
> Could the file system be corrupted?
i have no idea ! how can i know if it is corrupted ?

---

### Post by simo2 on 2018-04-03
> **HermanAB said:**
> Hmm, an RPi runs off a SD card.  It may have a  faulty block.  You probably need to re-install on a new SD card to fix  this issue.
the OS runs over a USB stick

---

### Post by TheFu on 2018-04-03
> **simo2 said:**
> i have no idea ! how can i know if it is corrupted ?

Well, on a r-pi, I'd just reinstall.  It isn't like anyone keeps anything important on one of those.

---

