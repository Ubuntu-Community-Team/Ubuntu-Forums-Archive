---
title: "LXD Issue with 32bit ISO"
date: 2024-07-14
forum: General Help
---

### Post by Nattereri on 2024-07-14
I am having an issue where I cannot get a VM to  boot from Windows 7 ISO files that are for 32 bit editions. I can get  the 64 bit editions ISO files to boot.
 I am using Ubuntu 24.04 on the host with the snap version of LXD 5.21.1 LTS.
 I cannot find any errors in the journalctl ouput. The console display  will flash a message “Waiting for display 1…” and then return to the  Boot Manager screen.
 I am creating the VM with this command: lxc init --vm --empty
I then use profiles to set cpu and memory limits, the paths to the ISO  images for Windows 7 and virtio drivers. The final configuration is:
architecture: x86_64
config:
limits.cpu: “2”
limits.memory: 4GB
raw.apparmor: /mnt/sambaserver/** rwk,
raw.qemu: -drive file=‘/mnt/sambaserver/Windows 7/en_windows_7_sp1_x86.iso’,index=0,media=cdrom,if=ide
-drive file=‘/mnt/sambaserver/Windows 7/virtio-win-0.1.173.iso’,index=1,media=cdrom,if=ide
-cpu host
security.secureboot: “false”
volatile.cloud-init.instance-id: fd1ef8c6-0090-4c3a-ad4c-f216752dfe18
volatile.eth0.host_name: tap4fe726bb
volatile.eth0.hwaddr: 00:16:3e:99:5e:f4
volatile.last_state.power: RUNNING
volatile.last_state.ready: “false”
volatile.uuid: 42002c23-0f58-42ca-982b-ed800b53ba70
volatile.uuid.generation: 42002c23-0f58-42ca-982b-ed800b53ba70
volatile.vsock_id: “495110574”
devices:
eth0:
name: eth0
network: lxdbr0
type: nic
root:
path: /
pool: default
size: 60GiB
type: disk
ephemeral: false
profiles:
 
[LIST]
[*]default
[*]windows-7-pro-x86-install
[*]vm-small
stateful: false
description: “”
[/LIST]
 I have tried using the --debug option on lxc but I did not see any  obvious errors. Of course I am not that proficient with LXD yet either.
 Any ideas why this would happen?

---

### Post by TheFu on 2024-07-14
If the underlying kernel is 64-bit, then the linux containers must be 64-bit too.  lxc is a linux container, not a VM.  The kernel is shared in Linux Containers.  They aren't "VMs".
There is no version of Ubuntu from 20.04 and later that is 32-bit. [https://www.omgubuntu.co.uk/2019/06/ubuntu-is-dropping-all-32-bit-support-going-forward](https://www.omgubuntu.co.uk/2019/06/ubuntu-is-dropping-all-32-bit-support-going-forward)

BTW, Support for Win7 ended in 2020, so you'll find nobody able/willing to help here. Sorry.

I do have a Win7 32-bit install (thanks for the gift MSFT!) that I run inside a KVM/QEMU virtual machine.  It hasn't been on a network since MSFT changed their EULA around 2015.

---

### Post by Nattereri on 2024-07-17
I found the answer by reading the actual LXD manual. (Image that.) You can run 32 bit WIndows 7 in a LXD VM if you change the default qemu configuration using raw.qemu.conf. Although it looks like I will be learning how to do the same using QMP in the near future.
I got as far as getting the ISO to boot and install but the graphics is stuck at 640x480 and 8 colors. The default video adapter only has 256K of memory assigned to it so I will have to figure out how to create a whole new profile for the raw.qemu.conf settings.

---

### Post by TheFu on 2024-07-17
LXD is a manager only.  LXC, which is what most people run under LXD, is for linux containers only. Windows won't run.  I suppose LXD can manage QEMU or KVM VMs too.  The only people I've heard doing that where the LXD people or shops that started with containers and LXD before going with full VMs.  Of course, there are exceptions.  There are many things to like about LXD.  

Instead of LXD, people use libvirt with the different front-ends like virt-manager or virsh.  On Linux, I've never seen any VM host provide more than 128MB of videoRAM.

I've never heard of QMP.  Looked it up.  Seems specific to QEMU.  Seems odd to choose LXD which can control lots of different VMs and Containers, then to consider QMP which would be specific to QEMU.  I suppose, if you need to use QEMU to have non-KVM VMs running with other CPUs emulated, perhaps MIPS and Arm or one of the other 20+ CPU types that aren't running native on the physical hardware, that could make sense.  I was a cross-platform developer before QEMU existed, so we had the actual systems to do our testing.  Most of the time, we didn't cross-compile for the target hardware. We'd install development tools on those other systems and port the code.  Of course, there were a few platforms where none of the dev tools had been ports, so cross-compiling was the only way.  Did that for about 5 yrs for 1 extremely specialized type of hardware.

I've always found the LXD documentation to be full of stuff I wasn't seeking, but never the stuff I needed to know.  Heck, I've been unable to figure out how to get LXD to use LVM without thin provisioning.  They really, really, really, want people to use ZFS.

Anyway.  Reads like you are using QEMU to run Win7.  Without KVM, you are getting significantly worse performance.  QEMU is all software.  QEMU+KVM takes advantage of hardware support for fast context switching.  Hummmm.  I do remember that for 32-bit guests, for many workloads, software-based virtualization was faster than using KVM.  I don't remember that applying to QEMU, but for Pre-Oracle VirtualBox, it was commonly stated.  Maybe it did?  IDK.  l I never tested it, once my systems supported KVM.  I always enabled VT-x support.

---

