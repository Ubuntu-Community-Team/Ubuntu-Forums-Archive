---
title: "Vmware player won't work after kernel update"
date: 2007-02-14
forum: General Help
---

### Post by bodycoach2 on 2007-02-14
After the recent kernel update, I try to open Vmware player, select the .vmx file I'm using, and it gives error messages, "vmmon missing"

I've tried uninstalling and reinstalling vmware player from synaptic, but still get the same message.

Any ideas?

---

### Post by tribble222 on 2007-02-14
have you run vmware-config?

---

### Post by veloce on 2007-02-14
I think you'll find that VMware Player doesn't come with vmware-config.  You may be out of luck until the vmware player code is updated for the new kernel.

My solution is to use vmware server.

---

### Post by bodycoach2 on 2007-02-14
I backtracked to the former kernel, and vmware worked just fine. After reading a few threads about the latest kernel, I deleted it, and am sticking with the ...27 version.

My girlfriends computer kept locking up after the update. Getting rid of the ...28 kernel fixed it. 

I wonder what the bugs were in the new kernel?

---

### Post by veloce on 2007-02-14
Whereas my upgrade of the kernel has caused no issues at all.

---

### Post by ximok on 2007-02-15
This is actually a fairly common problem.  

Basically what happens is the kernel gets updated, vmware *might* get updated, but then the vmware-kernel-modules package does not get upgraded because it is dependent on the kernel update.

If the vmware-kernel-modules do not keep up to date with the latest kernel version, it can leave you dead in the water till someone updates that package.

Try upgrading vmware-kernel-modules manually (apt-get install vmware-kernel-modules) and see if that works.  Oh, do a reboot FIRST so you are using your new kernel, then try manually updating.

I have a large installation of vmware-player boxes and have decided NOT to use the prebuilt package that comes with ubuntu.  Instead, I have resorted to using a script and manually updating it myself.  It's a lot of extra work, but I can make the modules update via a script if the kernel gets an update.

---

### Post by Moulton on 2007-02-17
It's a common -- and annoying -- problem.

Most of the time, when there is a kernel upgrade in the software update (security) channel, the corresponding kernel module upgrade for VMware is not yet available for the new kernel.

And then the package updaters fruitlessly keep trying to fix the problem, running the doomed post-install script over and over whenever some unrelated package is updated or installed.

This is the case for the most recent kernel upgrade for Dapper.  The kernel upgrade to 2.6.15-28 leaves VMware out in the cold, as the requisite kernel modules are only available up through 2.6.15-27.

The temporary fix is to boot up with the previous kernel.

But I would be grateful if those who are responsible would either keep these modules in sync, or revise the post-install scripts so that one doesn't have to type in so many repetitious answers to the questions about configuring VMware components.

---

### Post by gjtoth on 2007-02-17
Same thing has happened to Parallels.  Won't compile either.  Soooo, we're stuck until they (Parallels) come out with a new version that is compatible with the new kernel.

---

### Post by praxis22 on 2007-02-17
The Fiesty kernel broke vmware for me, this is how I fixed it:

[http://ubuntuforums.org/showpost.php?p=2169172&postcount=838](http://ubuntuforums.org/showpost.php?p=2169172&postcount=838)

It's basically a complete re-install, (though your existing VM's will be fine) you have to patch the module source, and rebuild the module.

---

### Post by wasteed on 2007-02-17
> **bodycoach2 said:**
> I backtracked to the former kernel, and vmware worked just fine. After reading a few threads about the latest kernel, I deleted it, and am sticking with the ...27 version.

My girlfriends computer kept locking up after the update. Getting rid of the ...28 kernel fixed it. 

I wonder what the bugs were in the new kernel?

I also had to backtrack to the -27 kernel, when after 3 days of use with the new kernel, I found X was using 99% CPU and 50% of the available memory (1GB RAM and 1GB swap). -27 has no such problem...

---

### Post by ximok on 2007-03-05
What I don't understand, is why don't the vmware-player maintainers just solve the problem and require vmware-player have the kernel source and package the vmware-config script.  That way, you can fix it whenever you upgrade the kernel.

Or at least provide an alternate version of the package.  (Who knows, maybe there is an alternate version)

---

