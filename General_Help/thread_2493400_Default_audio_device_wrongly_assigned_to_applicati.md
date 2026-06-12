---
title: "Default audio device wrongly assigned to application"
date: 2023-12-14
forum: General Help
---

### Post by dansity on 2023-12-14
Hello,

I have this running issue for a while and I haven't found a working solution.
I have KVM with virt-manager virtual machine where I'm using MS teams for work. I have a bluetooth headphone to talk. Obviously I need this BT headphone to be the default for KVM.
If I turn on my computer, connect the headphone then start KVM it is ok, KVM uses the default audio device which is the headphone. But if I for example put the machine to suspend, turn it on and the headphones are not connected it will default to my speaker and no matter how many times I set it to my headphone or define my headphone to be the default audio device when sound appears and virt-manager appears at the application list and it defaults to my speaker.
Please note that virt-manager is not permanently displayed at the applications tab in the sound settings of KDE, only when there is a sound activity on it. So it disappears every time I finish a call and when it reappears it is again uses the wrong audio device.
It is really grinding my gears, I'm looking for a permanent solution.

Kubuntu 23.10

---

### Post by TheFu on 2023-12-21
You can setup USB passthru for different devices using the USB ID of that device inside the machine settings. Will that work?
Of course, this is exclusive use, so the host system cannot use it or the VM will refuse to start.

I'm assuming the headphone has some sort of USB connector, if not real, at least virtual inside the computer. I don't use bluetooth (terrible security) , so all of this is just a guess.

---

### Post by SeijiSensei on 2023-12-21
I'm sure the answer is yes, but just in case, did you look at System Settings > Audio in KDE to define the default device?

---

### Post by MAFoElffen on 2023-12-21
LOL. Not really an applications assignment issue... As hardware virtualization is not just "an application".
> **TheFu said:**
> You can setup USB passthru for different devices using the USB ID of that device inside the machine settings. Will that work?
Of course, this is exclusive use, so the host system cannot use it or the VM will refuse to start.

I'm assuming the headphone has some sort of USB connector, if not real, at least virtual inside the computer. I don't use bluetooth (terrible security) , so all of this is just a guess.
That is what I do if I need to. I use my USB gaming headset... and pass it through to the VM.

That just requires that you make some changes right before you start up the VM, then change it back right after you shut it down. Then it can be used by both the Host and VM... Just not shared between the two at the same time. Manually doing that each time is possible, works, and is manageable. Not real convenient, but still, it's much less work than the alternative.

The alternative to make that very much more complicated to setup, you can create pass-through scripts in /etc/libvirt/hook/qemu.d/<machine_name>... /<timing_state> where you create vfio pass-through scripts there, to release the hardware from the host, commit it to specific VM's, where when that VM starts, then it releases the hardware asset from the VM, and commits it back to the host, when that VM is shut down. That process is very hard to setup and get working right. It's a lot of trial and error.

That process is "possible"... But not for the faint of heart without some very advanced skills to make that happen. Is convenient, but is a "whole lot of work" to get setup properly. Just because that is possible doesn't make that a good idea.  If it breaks, it is a very big, very frustrating mess.

---

