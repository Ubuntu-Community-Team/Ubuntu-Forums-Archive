---
title: "How disable kernel module chromeos_pstore ?"
date: 2022-10-09
forum: General Help
---

### Post by aug7744 on 2022-10-09
Hello.
Using kernel 5.19.14.
In OS starting is showed "loading kernel module chromeos_pstore".
How disable and remove kernel module chromeos_pstore ?

Thanks for reply.

---

### Post by TheFu on 2022-10-09
blacklist the module in /etc/modprobe.d/
There are lots of examples in there.

---

### Post by aug7744 on 2022-10-10
Have done it and not work.

Also done

/etc/modprobe.d/chromeos.conf"
blacklist chromeos_acpi
blacklist chromeos_laptop
blacklist chromeos_privacy_screen
blacklist chromeos_pstore
blacklist chromeos_tbmc

not work too
OS is starting showing "loading kernel module chromeos_pstore".
That is recent ... was added in kernel 5.19.14 ?
Is useless for PC x86.
Any other way to disable it ?

---

### Post by &amp;KyT$0P# on 2022-10-11
Ah, you're not seeking to disable the kernel module, you want to disable the systemd service "Load Kernel Module chromeos_pstore".

Try
```
sudo systemctl disable modprobe@chromeos_pstore.service
sudo systemctl mask modprobe@chromeos_pstore.service
```
Then reboot.

Does this help?

---

### Post by #&amp;thj^% on 2022-10-13
Nice catch halogen2, i found it UN-nessacary a while back, now that's something I just do
```
>> systemctl status modprobe@chromeos_pstore.service
&#9675; modprobe@chromeos_pstore.service
     Loaded: masked (Reason: Unit modprobe@chromeos_pstore.service is **masked**.)
     Active: inactive (dead)

``` 
It would be helpful if the OP would confirm.

---

### Post by aug7744 on 2022-10-14
@ TheFu

Thanks againg for your good deeeds replying me.

trying blacklisting in path below not work
/etc/modprobe.d/

@halogen2
About

sudo systemctl disable modprobe@chromeos_pstore.service
sudo systemctl mask modprobe@chromeos_pstore.service

I have done the commands above
In /etc/systemd/system/ not had any reference for pstore.service

@1fallen

Doing command
systemctl status modprobe@chromeos_pstore.service

modprobe@chromeos_pstore.service
Loaded: masked (Reason: Unit modprobe@chromeos_pstore.service is masked.)
Active: inactive (dead)

In dmesg log not any reference for chromeos_pstore

The "chromeos_pstore" was added recently in 5.19 (5.19.12 or 5.19.14 ?)
I see being useless for PC computers because is related for chrome os computers.

Having an OS configured only with details you need disabling if possible all useless resources is the path to go.

---

### Post by #&amp;thj^% on 2022-10-14
> **aug7744 said:**
> 
In dmesg log not any reference for chromeos_pstore

The "chromeos_pstore" was added recently in 5.19 (5.19.12 or 5.19.14 ?)
I[B][U] see being useless for PC computers because is related for chrome os computers.
[/U][/B]
Having an OS configured only with details you need disabling if possible all useless resources is the path to go.

That's my thought as well, I'll not take the freeloaders along with my OS. LOL :D
```
uname -r
6.0.1-zen2-1-zen
```

---

### Post by aug7744 on 2022-10-20
**@** [URL="https://ubuntuforums.org/member.php?u=2034672"][B][COLOR=#000000]halogen2

[/COLOR][/B][/URL]What is the meaning of "@" between modproble and chromeos_pstore ? Means to blacklist any service or module with *chromeos* ?

---

### Post by ActionParsnip on 2022-10-20
Found this:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1982462](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1982462)

---

### Post by &amp;KyT$0P# on 2022-10-20
> **aug7744 said:**
> What is the meaning of "@" between modproble and chromeos_pstore ?

It means [FONT=Courier New]modprobe@chromeos_pstore.service[/FONT] is a dynamically generated service generated from the [systemd template]("https://ibug.io/blog/2019/07/systemd-service-template/") [FONT=Courier New]modprobe@.service[/FONT]

---

