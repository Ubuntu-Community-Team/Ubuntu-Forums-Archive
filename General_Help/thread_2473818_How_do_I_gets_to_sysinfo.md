---
title: "How do I gets to sysinfo?"
date: 2022-04-14
forum: General Help
---

### Post by Tom_Carr on 2022-04-14
On my ubuntu 18.04, I just  typed in "sysinfo"  and it came up.  This doesn't work on my 20.04 machine.  How do I get sysinfo on 20.04 and later versions?

---

### Post by TheFu on 2022-04-14
There are many different ways to gather system information.

**lshw **
**inxi -Fxxz**
[https://github.com/UbuntuForums](https://github.com/UbuntuForums) has a sys-info script.

On a 20.04 system, when I type **sysinfo**, I see
```
$ sysinfo

Command 'sysinfo' not found, did you mean:

  command 'xsysinfo' from deb xsysinfo (1.7-9build1)
  command 'rsysinfo' from deb rstat-client (4.0.1-9)

Try: sudo apt install <deb name>
```
So, there appear to be 2 packaged options.

---

### Post by Tom_Carr on 2022-04-14
I didn't ask my question clearly.  I didn't mean going into the terminal and typing sysinfo.  I meant in the GUI, hitting the ubuntu button and which brings up the "type to search" box at the top, then typing "sysinfo" into that box.

---

### Post by Tom_Carr on 2022-04-14
I went into terminal on the 20.04 and it told me sysinfo was not installed.  I installed it and now it works fine.  Thanks for your help.

---

### Post by TheFu on 2022-04-14
> **Tom_Carr said:**
> I went into terminal on the 20.04 and it told me sysinfo was not installed.  I installed it and now it works fine.  Thanks for your help.

If solved, please use the Thread Tools button and mark it _SOLVED_ to help others.

BTW, if you install **inxi** and **lshw** now, should any issues come up in the future, people here will be able to provide exact options to provide the information desired in a concise way.

---

### Post by GhX6GZMB on 2022-04-14
Actually 'sysinfo' is not the right package. The correct one is called 'hardinfo'. It's often already installed as "System Profiler and Benchmark".
I don't know what you've installed.

---

### Post by Tom_Carr on 2022-05-17
I installed hardinfo and it does everything I want.  It is much better than the old sysinfo.  Thanks for your help.  I am closing the thread.

---

