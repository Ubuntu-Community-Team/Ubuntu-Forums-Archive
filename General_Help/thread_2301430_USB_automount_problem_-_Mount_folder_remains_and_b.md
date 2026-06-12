---
title: "USB automount problem - Mount folder remains and blocks"
date: 2015-11-02
forum: General Help
---

### Post by andreas50 on 2015-11-02
I am dealing with the following scenario:

On a device running Ubuntu 14.04, multiple USB drives (ext4) which all have the same label may be inserted and removed at any time. This part works fine so far.
However, the device will sometimes be shut down through loss of power by nature of its usage environment (Safe shutdown cannot be guaranteed)

In this case, sometimes (not always, but especially if the usb device is switched before the restart) the mount point of the USB device (following the scheme **/media/username/label**) REMAINS after the device is powered on again.
This leads to the usb device then being mounted along the lines of **/media/username/label1**, and in repeated cases ../label2 and so on.

These dead folders remain indefinitely until I remove them manually. After doing this, a restart fixes the problem. 
However, I want to avoid this happening in the first place. It seems like an obscure bug in nautilus or whatever is doing the automounting. 

Any ideas?

---

### Post by col48 on 2015-11-02
I can't give a full answer (beyond my expertise!) but I'm not convinced it is actually a bug so much as a side-effect of the environment you describe.

This link to a somewhat related (but old) problem someone was having with mounting and unmounting usb sticks says something about how the mechanism operates, and that it is at a deeper level than Nautilus.  Nautilus is merely watching for the creation, replacement and destruction of directories, files, links etc and adapting its display accordingly.
[HTML]https://www.linuxquestions.org/questions/linux-hardware-18/how-does-automount-unmount-work-for-usb-memory-sticks-666983/
[/HTML]

What is happening is that the unmount you need is not happening because of the power cut.

Perhaps the rationale for what you see is it would be difficult for Linux to ascertain that the repowered device is actually the same as it last knew (not just the same physical device but also unaltered for instance by something done on a different computer), so using a new mount point is the safest thing to do?
Perhaps there is something about an old mount point in these circumstances which could cause damage to the data on the device?  Might it be holding knowledge of unwritten buffers which an attempt to access the device would trigger?
I do not know.

It looks like a cautious approach to what may be a difficult question.
You could build a batch which could delete these dead mount points at a single click at will.

---

### Post by andreas50 on 2015-11-04
I'm afraid I'll have to look into making the operating system readonly, putting the changeable data in a writeable partition. That would not be a problem for usability in this scenario. 
That way, the mount point should disappear by default, as it can't be remembered at all, right?

---

### Post by col48 on 2015-11-04
I am not convinced that would work.

1. If you make /media/username read-only, it will not be possible to create /media/username/label (or to write to it if it already exists) so the USB could not be mounted, as far as I understand it.
2. Depending how wide your definition of OS is, you may inhibit the operation of other software which likes to keep track of (say) recent files accessed and preferences chosen.
3. If you make the whole OS read-only, you won't be able to take updates easily, which may cause issues in the future.

Wanted: help more expert than me!

---

### Post by bab1 on 2015-11-04
> **andreas50 said:**
> I am dealing with the following scenario:

On a device running Ubuntu 14.04, multiple USB drives (ext4) which all have the same label may be inserted and removed at any time. This part works fine so far.
However, the device will sometimes be shut down through loss of power by nature of its usage environment (Safe shutdown cannot be guaranteed)

In this case, sometimes (not always, but especially if the usb device is switched before the restart) the mount point of the USB device (following the scheme **/media/username/label**) REMAINS after the device is powered on again.
This leads to the usb device then being mounted along the lines of **/media/username/label1**, and in repeated cases ../label2 and so on.

These dead folders remain indefinitely until I remove them manually. After doing this, a restart fixes the problem. 
However, I want to avoid this happening in the first place. It seems like an obscure bug in nautilus or whatever is doing the automounting. 

Any ideas?
The system is working correctly.  All media that is mounted automatically via a USB port and not included in the /etc/fstab file uses these 2 components: ***udisks2*** and ***udev***

The part that udisks2 provides is the interfaces to enumerate and perform operations on disks and storage devices.  See [**here**]("http://udisks.freedesktop.org/docs/latest/udisks.8.html") for the details.

The second part is the udev component.  Udev is a device manager for the Linux kernel.  See [**here**]("https://wiki.archlinux.org/index.php/Udev") for the details.  Pay attention to the section on udev rules.

Do not under any circumstances make the OS read only.  The system will fail for sure.

I think you are better off by mounting the partition using ***fstab***.   It is consistent and you can mount the partition via the partition label to a specific mount point. (/media/<label>).  The only requirement is that you unmount the partition before removing it and explicitly mounting the new device's partition.  I do this via bash scripts that are triggered by icons on the desktop.

---

### Post by andreas50 on 2015-11-06
> **bab1 said:**
> 
I think you are better off by mounting the partition using ***fstab***.   It is consistent and you can mount the partition via the partition label to a specific mount point. (/media/<label>).  The only requirement is that you unmount the partition before removing it and explicitly mounting the new device's partition.  I do this via bash scripts that are triggered by icons on the desktop.
I'm not quite sure what you mean here - How would I guarantee an unmount? The USB drives will be hastily removed by users who have no way of leaving the on-screen application and unmounting anything, let alone running a bash script. And if the device is powered down abruptly, no safe unmount can happen either. Maybe I'm misunderstanding what you meant.

Edit: I've gotten far with a workaround. The application running on the Ubuntu device checks if additional iterated mount points exist, unmounts them and deletes the broken original one. The system can then recognize the USB device with the original label again. The only problem is that mount doesn't work after umount for some design decision reason. The icon of the USB drive is still there, and it gets remounted when I click on it, but I'd like to force this remounting with a command in the background instead of GUI interaction. Any ideas?

---

### Post by bab1 on 2015-11-06
> **andreas50 said:**
> I'm not quite sure what you mean here - How would I guarantee an unmount? The USB drives will be hastily removed by users who have no way of leaving the on-screen application and unmounting anything, let alone running a bash script. And if the device is powered down abruptly, no safe unmount can happen either. Maybe I'm misunderstanding what you meant.

You can't guarantee that the device will be unmounted cleanly when than there is a powercut.  However, you can insure where the partitions is mounted  despite having a powercut.  I have one script that mounts and unmounts multiple partitions at one time.  Click the icon once and the partitions are mounted.  Click the icon again and they unmount.  The user just needs to know that clicking the icon provides availability and removes it also.
> 

Edit: I've gotten far with a workaround. The application running on the Ubuntu device checks if additional iterated mount points exist, unmounts them and deletes the broken original one. The system can then recognize the USB device with the original label again. The only problem is that mount doesn't work after umount for some design decision reason. The icon of the USB drive is still there, and it gets remounted when I click on it, but I'd like to force this remounting with a command in the background instead of GUI interaction. Any ideas?
I'd have t see what you are actually doing.  Can you provide some code?

---

