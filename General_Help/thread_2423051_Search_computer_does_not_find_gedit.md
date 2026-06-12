---
title: "Search computer does not find gedit"
date: 2019-07-16
forum: General Help
---

### Post by Roland_Msl on 2019-07-16
Suddenly nothing to read in the menus. They drop down, there are some arrows, but nothing to read.
I restarted my Ubuntu 16.04 notebook.

Now I noticed, that "Search Your computer" does not find gedit or simple scan.

I started "Ubuntu Software" and typed gedit. Only the description ans the "install" button appeared. I clicked install.
"Ubuntu Software" finds "Simple scan". There is like expected the "Lounch" and the "Remove" button.

Still "Search Your computer" finds not any program.

Any idea how to fix this?

---

### Post by TheFu on 2019-07-16
Sounds like the disk drive is failing. Check the system logs and SMART data for the disk errors.  Backup your data ASAP.

---

### Post by Roland_Msl on 2019-07-17
> **TheFu said:**
> Sounds like the disk drive is failing. Check the system logs and SMART data for the disk errors.  Backup your data ASAP.

I typed XMAN and got
Warning: Cannot convert string "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct

A small window opened like described, but what now?

---

### Post by dino99 on 2019-07-17
Have you made some custom tweaks before getting that issue ? (like changing themes/fonts, or mixing DEs)
"journalctl -b" should show some warnings/errors  to help you solving that problem.

---

### Post by TheFu on 2019-07-17
> **Roland_Msl said:**
> I typed XMAN and got
Warning: Cannot convert string "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct

A small window opened like described, but what now?

What does my avatar image have to do with YOUR question?  Not that it matters, but click on one of the 3 "buttons." Yes, those are buttons.

Did you check the other things suggested?

---

### Post by Roland_Msl on 2019-07-17
> **dino99 said:**
> Have you made some custom tweaks before getting that issue ? (like changing themes/fonts, or mixing DEs)
"journalctl -b" should show some warnings/errors  to help you solving that problem.
This command brought :

founder@founder-Aspire-ES1-331:~$ journalctl -b
ul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/cuse, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/autofs, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/btrfs-control, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/userio, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/vfio, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/vfio/vfio, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/vhci, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/uhid, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/vhost-net, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/snd, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/snd, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/snd/timer, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd-tmpfiles[326]: Unsafe symlinks encountered in /dev/snd/seq, refusing.
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd[1]: systemd-tmpfiles-setup-dev.service: Main process exited, code=exited, status
Jul 16 19:27:56 founder-Aspire-ES1-331 systemd[1]: Failed to start Create Static Device Nodes in /dev.

Where could I find this data more easy to copy and view?

I can start gedit by software or terminal
Click right on "Search Your computer" click Applications - nothing found

---

### Post by TheFu on 2019-07-17
dmesg is one command.

/var/log/ That's where all the system logs are.  You can filter using grep, egrep or learning to use journalctl.  All of them have manpages (that xman command is 1 interface into it) which explain how to sue each tool.
I use 
```
sudo egrep -i 'warn|error' /varlog/*g |more
```
to search all the current logs for warnings and errors.

Text is king on Unix systems and there are 100+ different text handling tools which can be used together to do pretty much anything you like.  With text processing, you can redirect output to files for viewing or more processing if you need multiple steps in the text processing.  It is a completely different way of thinking compared to non-Unix-based OSes.

I suppose there are other ways to gather the same information. I just don't know them. Sorry.

---

### Post by Roland_Msl on 2019-07-17
I copied Your command in the terminal "grep: /varlog/*g: No such file or directory

---

### Post by TheFu on 2019-07-17
What, exactly did you enter - since my example didn't use grep.

---

### Post by CatKiller on 2019-07-17
> **TheFu said:**
> What, exactly did you enter - since my example didn't use grep.

**egrep** is the same as **grep -E**. The error is because you've got **/varlog/** rather than **/var/log/**.

---

### Post by Roland_Msl on 2019-07-17
> **TheFu said:**
> What, exactly did you enter - since my example didn't use grep.
sudo egrep -i 'warn|error' /varlog/*g |more

---

### Post by Roland_Msl on 2019-08-21
Suddenly, I restarted maybe 2 or 3 times in the last weeks, search is here again and works like usual.

---

