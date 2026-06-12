---
title: "Installing kubuntu 7.04 as kvm guest"
date: 2007-09-03
forum: General Help
---

### Post by Nuld on 2007-09-03
I'm trying to install Kubuntu as guest in kvm but always get an error directly after I start the virtual machine. I'm using the alternate installation CD, since I read that the normal installation doesn't work with kvm.

$ kvm -m 384 -cdrom <path>/kubuntu-7.04-alternate-i386.iso.iso -boot d kubuntu-feisty.img 
exception 12 (0)
rax 00000000000007a0 rbx 0000000000040080 rcx 0000000000002000 rdx 0000000000016600
rsi 00000000ffff0800 rdi 0000000000040000 rsp 0000000000087bdc rbp 0000000000000000
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000a4bc rflags 00033206
cs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (18850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fa4d1/37
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
Aborted (core dumped)

Any ideas why this isn't working? I didn't have any problems to get WinXP to work in KVM.

Thanks!

---

### Post by Nuld on 2007-09-04
No ideas anyone?

Could someone who has gotten it to work tell me if he/she has done something different? For example which installation CD was used.

---

