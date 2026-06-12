---
title: "How to prevent Ubuntu upgrade from overwriting *.dtbo files"
date: 2022-01-27
forum: General Help
---

### Post by tc2020 on 2022-01-27
Hello,

I would like to know if there is a way to prevent Ubuntu upgrade from overwriting my version of specific *.dtbo files in /boot/firmware/overlays directory?. Until now, I have to copy those 4 files after each upgrade. If not, my embedded device would not work as intended due to specific hardware requirements.

If copying .dtbo files is the only way then is there a way to avoid system reboot after? 

Any help would be greatly appreciated. Thank you.

---

### Post by TheFu on 2022-01-28
If it was me, I'd create a script and keep copies of the files elsewhere.

You can try setting the files to "immutable"  - the **sudo chattr +i /path/to/file** will do that. Beware, that this can cause problems because when the files do need to be updated and that fails, the update process will fail. You'll be stuck and will have likely forgotten the command was used.

Another option is to make a separate partition for the entire directory and mount it read-only in the fstab. The same problem with updates failing will happen. You'll have to remember to remount -o rw.  This can be done on the system while it is running.

Neither of those options is great. Sorry.

---

### Post by tc2020 on 2022-01-28
Thanks for the suggestion. Right now we keep our version of *dtbo, *.conf, *.yaml, and other files in a separate directory. On reboot, except *.dtbo's, we copy them over to their respective places to make sure the system runs our version. Because we let the system auto upgrade, our application stops working because the upgrade replaces our *.dtbo's. In this case, we have to copy these files over and reboot then everything is fine after. 

So what we want to do is to find out two things:
1). A way to load *.dtbo files without having to reboot. Any idea on how to do this?. If this works, we simply copy them over on each reboot. 
2). We write a script to check kernel version. If that changes, then copy *.dtbo's and do a reboot. Any idea on where to read this version (is uname -a the only way?)

Thanks.

---

### Post by schragge on 2022-01-28
> **tc2020 said:**
> (is uname -a the only way?)
**uname -r** should be enough, no?

---

### Post by TheFu on 2022-01-28
There is a file that updates should create when a reboot is needed.
**/var/run/reboot-required**
I test for this file to decide if a reboot is needed post patch cycle. Nothing else.
I don't care what the reason is - new kernel, new libc, whatever. Doesn't matter. If the file exists, then I have a reboot process since nearly all my systems run virtualized.  If the VM hostOS needs rebooting, no need to reboot the guest VMs.

I cannot answer the embedded systems question. Sorry.  I had to look up what a dtbo file is today.

---

### Post by tc2020 on 2022-01-31
yes, **uname -r **should do. The -r option provides a cleaner string for kernel version, so we will read and store it in a file for use as reference to copy dtbo's and reboot. 
At the moment my device does not have /var/run/reboot-required, I assume it exists only when reboot is required. I will check it out next time to see what the file looks like.
Thanks for your help.

---

### Post by TheFu on 2022-01-31
/var/run/reboot-required is empty. This is very common to have an empty file as a flag that something happened or needs to happen. The fact that it exists at all means something specific. Just test for the existence of the file in your script.

I vaguely remember seeing a file in the same directory which provided reasons for why a reboot was needed. For my needs, that didn't matter. It is a binary choice - reboot needed or not.

---

### Post by schragge on 2022-02-01
```
[COLOR=green]$[/COLOR] cat /var/run/reboot-required[COLOR=green]
*** System restart required ***
$[/COLOR] cat /var/run/reboot-required.pkgs[COLOR=green]
linux-image-5.4.0-97-generic
linux-base[/COLOR]
```

---

