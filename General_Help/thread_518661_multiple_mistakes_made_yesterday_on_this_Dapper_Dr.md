---
title: "multiple mistakes made yesterday on this Dapper Drake LTS"
date: 2007-08-06
forum: General Help
---

### Post by bowie101 on 2007-08-06
Didn't know which topic to put this under, as it could fit in a few of them, I think. If we want to move this to the most appropriate topic, then let me know which one will work the best

-------------------------------------------------------------------------------------------------

Just yesterday, this Dapper Drake (LTS) laptop was working fine. 

then, 

1)I ran update manager, without looking and scrutinizing over what I was updating. I think it did include something with the linux kernel and 31 other items. Damn, you have to look over every one! 

2) after the blackout, later that day, the computer turned back on, when the electric came back. But then the wireless conncection , with the USB wireless, Airlink 101 model no. AWLL3026/NA, stopped working. Indeed, I look in networking, and there is no configuration anymore for a wireless devise, even though the Airlink 101 is sticking in the USB port, with it's neon blue light on. not flashing, as it should to tell me it's getting signals, but on.

3) to try and "correct" the problem, i start tooling around in the terminal, looking for things, that don't exist. then i go to the root ( / )
and I see "vmlinux" and "vmlinux.old", that are 2 symbolic links to booting sequences.  "old" points to  2.6.17-11-generic and the new one points to 2.6.17-12-generic . so stupid me, I try to switch the 2. making old be the -12 and the new be -11 using the cp command. 

4) now I try to boot, and nothing happens. it can't even boot. get's stuck at the mouse splash screen

5) try to boot on the 2.6.17-12-generic  recovery mode, and it gets as far as looking for a root directory aqnd then gets stuck. 

6) try to boot with 2.6.17-11-generic  and that works. but again, still no wireless connection, and if i look at the vmlinuz files that i messed around with in the root directory, they appear to be back to normal. with vmlinuz back to pointing to 2.6.17-12-generic , as if i never touched them (but there is an extra vmlinux.old2 file there, remnants of me trying to switch both around, and needing a temporary holding spot.)

So as it stands now, there is no wireless, and i have to boot with the old kernel version to see anything, and i don't see how i can go back and fix my mistakes, if they appear corrected already (but while booted under the old kernel version, which i think may be significant, but what the hell do i know, at this point?)

HELP PLEASE. (again, if this thread should be moved to get help. let me know where. thanks, b.)

the laptop is a very old Toshiba laptop, used to have windows 98 on it.

---

### Post by mdurham on 2007-08-06
I think you can see which files were installed in Synaptic under File->history

---

