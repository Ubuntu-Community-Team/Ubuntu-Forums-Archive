---
title: "Odd Gnome Crash"
date: 2006-12-11
forum: General Help
---

### Post by thesquib on 2006-12-11
I seem to be getting a crash in Gnome(it restarts to the login screen). I am usually using Amarok, Firefox, and Skype 1.3. It happen twice in the last hour
Sometimes the screen just goes blank, other times the whole screen will distort (lines of colours) then go blank.. always coming back to the login screen.

Any ideas? I'm running the nvidia driver 96.29.. Not sure what else I can post apart from this:

I got this in the system log:
Dec 12 11:53:18 kernel: [17189697.824000] Bad pte = 5def6058, process = Xorg, vm_flags = 75, vaddr = b7cccec0
Dec 12 11:53:18 kernel: [17189697.824000]  <c014863d> __handle_mm_fault+0x7fd/0x840  <c014aef8> vma_link+0x38/0xb0
Dec 12 11:53:18 kernel: [17189697.824000]  <c014bccc> do_mmap_pgoff+0x52c/0x715  <c02c7ba9> do_page_fault+0x3d9/0x6e0
Dec 12 11:53:18 kernel: [17189697.824000]  <c02c77d0> do_page_fault+0x0/0x6e0  <c0103f7f> error_code+0x4f/0x60
Dec 12 11:53:18 kernel: [17189697.824000] VM: killing process Xorg



Thanks for any help...

---

### Post by ciscosurfer on 2006-12-11
That an nvidia beta driver, no?  I have a feeling it has to do with the fact that the nvidia driver is still in beta.

I don't know if this will help or not, but you can give these a try: [http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)
[http://ubuntuforums.org/showthread.php?t=278934&highlight=nvidia+binary+driver](http://ubuntuforums.org/showthread.php?t=278934&highlight=nvidia+binary+driver)

---

### Post by thesquib on 2006-12-11
I removed the nvidia driver using the method 2 uninstallation instructions (this was the method I used to install). I then installed the nvidia-glx package, and rebooted.

But it doesn't boot - it complains it cannot find the nvidia module (nvidia.ko)

I'm running with the nv driver for now...

---

### Post by thesquib on 2006-12-13
Anyone able to help with why I can't install nvidia-glx? It installs fine.. I do the xconfig.. then when I reboot / reload x it says it can't find the required nvidia.ko module... tried all sorts of stuff..

---

