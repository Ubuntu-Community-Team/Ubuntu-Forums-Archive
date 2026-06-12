---
title: "kvm issues"
date: 2008-05-07
forum: General Help
---

### Post by blazerguns on 2008-05-07
Hi Folks,

          I have been facing some problem with kvm. I have installed kubuntu hardy. I have Intel based hardware visualization support. I have enabled it on bios. I also have insmoded kvm module. My intention is to run my own custom kernel on kvm. I have a Fedora FS image to run it with.

#sudo kvm FedoraCore6-x86-root_fs Images/bzImage -append "root=/dev/hda" -initrd Images/initrd-2.6.25.img 
exception 13 (33)
rax 0000000000009000 rbx 0000000000000000 rcx 0000000000000000 rdx 0000000000000080
rsi 00000000ffff0000 rdi 000000000008fdba rsp 0000000000008ffe rbp 0000000000000000
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000fa42 rflags 00033006
cs 9020 (00090200/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 9000 (00090000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 9000 (00090000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 9000 (00090000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 9000 (00090000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 9000 (00090000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (fffbd000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fb1f2/30
idt 0/3ff
cr0 10 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0c 03 40 a0 3f --> ff ff 00 c8 30 0c 10 30 0c 3f 45 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aborted


Googling tells me its a intel real mode emulation problem.
[http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems](http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems)

Most workarounds suggested seem to indicate for installing some distro using kvm or running live cd. In my case i just want to boot using my fs and kernel image. Anybody aware of this? This setup used to work very well in open suse with qemu. Iam not able to get it working with qemu also.

---

### Post by RAOF on 2008-05-07
So, a couple of things:
1) Why are you running kvm as root?  It doesn't look like anything you're doing there needs superuser privs
2) From the linked page, does it work if you pass -no-kvm to kvm?
3) If yes above, you'll want to find out how to disable the splash-screens from the Fedora install.

---

### Post by blazerguns on 2008-05-07
ok, the same issue if i run as non-root
#kvm -m 512 -no-acpi FedoraCore6-x86-root_fs Images/bzImage -append "root=/dev/hda" -initrd Images/initrd-2.6.25.img
exception 13 (33)

with -no-kvm

blazerguns@varun-laptop:/home1$ kvm  -no-kvm FedoraCore6-x86-root_fs Images/bzImage -append "root=/dev/hda" -initrd Images/initrd-2.6.25.img
Ubuntu does not support running KVM without hardware acceleration. Sorry.


I would like to inform you that booting from live cd works like charm
#kvm -m 750 -cdrom /dev/cdrom -boot d virt-sys.img

any ideas?

---

### Post by blazerguns on 2008-05-07
wonder why it doesnt work with only qemu?

---

### Post by RAOF on 2008-05-07
> **blazerguns said:**
> wonder why it doesnt work with only qemu?

That is an excellent question.  Something which might be good in a launchpad.net bug report.  I'm not expert enough to be much more help, I think.

---

### Post by blazerguns on 2008-05-08
although i could not get it working with this FS, i managed to do with a new fedora fs img. Iam not sure if the fs is currupt, anyway i will post here if i find out the reason.

---

