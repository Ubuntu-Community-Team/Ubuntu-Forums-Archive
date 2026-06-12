---
title: "Ubuntu keeps freezing/crashing"
date: 2016-04-24
forum: General Help
---

### Post by dave2k1 on 2016-04-24
hello everyone,i have ubuntu 15.10 that i use on my netbook. the OS works fine except every now and then it locks up or crashes. i would have to do a hard reboot to get the OS working for the time being. this issue happens ALOT.... help!

---

### Post by Geoffrey_Arndt on 2016-04-24
What's the make, and model of the netbook??

   Important to know if it has at least 2 GiB of ram, and what kind of video system it has.   Many netbooks are lower end PC's that don't run modern OS's (Win8-10, Ubuntu Unity, etc.) very well.   So, generally, on netbooks, many people install a version of Linux with a lighter "footprint".    You might want to try Xubuntu 16.04 or even lighter, Lubuntu 16.04.    

These should work much better on the typical netbook.   (in other words, save your data, download and burn the new iso, and do a full-reinstall).

---

### Post by dave2k1 on 2016-04-24
i have the acer aspire v11 touch v3-111p-c3yj with 8gb ram. i think it uses an intel gfx card which i think is working.. it running ubuntu 15.10 64bit smooth except for the freezing/lock up every now and then.. where can i find the logs that is needed to show whats wrong?

---

### Post by oldrocker99 on 2016-04-24
Logs can be displayed with this command: ```
dmsg
```You may have to do a bit of searching, but it should show the error which is causing the lockup.

---

### Post by oldrocker99 on 2016-04-24
Logs can be displayed with this command: ```
dmsg
```You may have to do a bit of searching, but it should show the error which is causing the lockup.

---

### Post by QLee on 2016-04-25
> **dave2k1 said:**
> i have the acer aspire v11 touch v3-111p-c3yj

        Your problem seems similar to the problem with the so called "Bay Trail"processors. And , yes the N3530 in your system is one of the "Bay Trail"

        The "Bay Trail" processors and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have those random freezes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. Remember what you have done so you can remove it once they deal with the problem.

        If you encounter random freezes on a board that has one of those processors try adding intel_idle.max_cstate=1 to the GRUB line that boots your system. I wouldn't use it on any other family of processor. You can find a list at: [http://ark.intel.com/products/codename/55844/Bay-Trail](http://ark.intel.com/products/codename/55844/Bay-Trail)

        For example: in the file /etc/default/grub
        change the line
        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
        to
        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"

        and then
        ```


        sudo update-grub
```

        , reboot to use it. Test by opening a terminal and entering:
        ```


        cat /sys/module/intel_idle/parameters/max_cstate
```

        , it will return a number.


        It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

       If you choose to do the workaround, remember what you have done so you can remove it once they deal with the problem. <----------

---

### Post by dave2k1 on 2016-04-25
when i do 'dmsg' i get error code -

No command 'dmsg' found, did you mean:
 Command 'qmsg' from package 'torque-client' (universe)
 Command 'qmsg' from package 'torque-client-x11' (universe)
 Command 'dmesg' from package 'util-linux' (main)

---

### Post by dave2k1 on 2016-04-25
will definitely try that out QLee.. thank you so much for the prompt reply and answer!

---

### Post by dave2k1 on 2016-04-25
> **QLee said:**
> Your problem seems similar to the problem with the so called "Bay Trail"processors. And , yes the N3530 in your system is one of the "Bay Trail"

        The "Bay Trail" processors and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have those random freezes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. Remember what you have done so you can remove it once they deal with the problem.

        If you encounter random freezes on a board that has one of those processors try adding intel_idle.max_cstate=1 to the GRUB line that boots your system. I wouldn't use it on any other family of processor. You can find a list at: [http://ark.intel.com/products/codename/55844/Bay-Trail](http://ark.intel.com/products/codename/55844/Bay-Trail)

        For example: in the file /etc/default/grub
        change the line
        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
        to
        GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"

        and then
        ```


        sudo update-grub
```

        , reboot to use it. Test by opening a terminal and entering:
        ```


        cat /sys/module/intel_idle/parameters/max_cstate
```

        , it will return a number.


        It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

       If you choose to do the workaround, remember what you have done so you can remove it once they deal with the problem. <----------

i get a return of 1

---

### Post by QLee on 2016-04-25
Yes, you did it correctly, 1 is the result you wanted to see. Hopefully, you won't have any more trouble with freezes until the developers sort the problem out.

---

### Post by dave2k1 on 2016-04-26
> **QLee said:**
> Yes, you did it correctly, 1 is the result you wanted to see. Hopefully, you won't have any more trouble with freezes until the developers sort the problem out.


Qlee, it's looking good so far my friend.. you're the man!! quick question tho, how can i configure my gfx card? i installed the intel gfx drivers for ubuntu but dont know how to configure it.

---

