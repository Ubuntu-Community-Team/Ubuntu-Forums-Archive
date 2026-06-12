---
title: "Errors compiling kvm"
date: 2007-08-16
forum: General Help
---

### Post by jackn on 2007-08-16
I'd like to install KVM.

I've tried the [wiki ]("http://https://wiki.ubuntu.com/kvm?highlight=%28kvm%29")howto. Setting up went fine, but no OS I've tried (pclinuxos, fedora7 or... ubuntu feisty) worked. All aborted or hanged.

Now, this might be due to other reasons, but I thought I'd try compiling the latest release, as the repos have release 16, whereas the latest is 35. 

Before trying to build KVM 35, I (aptitude) remvoed the repo KVM.

The .configure step went fine, thanks to [advice]("http://ubuntuforums.org/showthread.php?t=110865") on how to allow KVM to use gcc-3.4, although the default Feisty gcc is 4.1 already.

'make', however, bombed.

Since "make's" output is way over my head, I post it here, although it is somewhat long. 
Please bear with me.

```
:~/kvm-35$ CC=/usr/bin/gcc-3.4 make
make -C user
make[1]: Entering directory `/home/jacknn/kvm-35/user'
/usr/bin/gcc-3.4 -I /usr/src/linux-headers-2.6.20-16-generic/include -MMD -MF ./.kvmctl.d -g -fomit-frame-pointer -Wall -m32       -c -o kvmctl.o kvmctl.c
kvmctl.c:26:2: #error libkvm: userspace and kernel version mismatch
In file included from kvmctl.c:37:
kvmctl.h:239: warning: "struct kvm_fpu" declared inside parameter list
kvmctl.h:239: warning: its scope is only this definition or declaration, which is probably not what you want
kvmctl.h:253: warning: "struct kvm_fpu" declared inside parameter list
kvmctl.h:318: warning: "struct kvm_cpuid_entry" declared inside parameter list
kvmctl.c: In function `kvm_create_vcpu':
kvmctl.c:219: error: `KVM_GET_VCPU_MMAP_SIZE' undeclared (first use in this function)
kvmctl.c:219: error: (Each undeclared identifier is reported only once
kvmctl.c:219: error: for each function it appears in.)
kvmctl.c: In function `kvm_create_memory_alias':
kvmctl.c:343: error: variable `alias' has initializer but incomplete type
kvmctl.c:344: error: unknown field `slot' specified in initializer
kvmctl.c:344: warning: excess elements in struct initializer
kvmctl.c:344: warning: (near initialization for `alias')
kvmctl.c:345: error: unknown field `flags' specified in initializer
kvmctl.c:345: warning: excess elements in struct initializer
kvmctl.c:345: warning: (near initialization for `alias')
kvmctl.c:346: error: unknown field `guest_phys_addr' specified in initializer
kvmctl.c:346: warning: excess elements in struct initializer
kvmctl.c:346: warning: (near initialization for `alias')
kvmctl.c:347: error: unknown field `memory_size' specified in initializer
kvmctl.c:347: warning: excess elements in struct initializer
kvmctl.c:347: warning: (near initialization for `alias')
kvmctl.c:348: error: unknown field `target_phys_addr' specified in initializer
kvmctl.c:348: warning: excess elements in struct initializer
kvmctl.c:348: warning: (near initialization for `alias')
kvmctl.c:343: error: storage size of 'alias' isn't known
kvmctl.c:353: error: `KVM_SET_MEMORY_ALIAS' undeclared (first use in this function)
kvmctl.c:343: warning: unused variable `alias'
kvmctl.c: In function `handle_io':
kvmctl.c:472: error: structure has no member named `data_offset'
kvmctl.c: At top level:
kvmctl.c:537: warning: "struct kvm_fpu" declared inside parameter list
kvmctl.c:538: error: conflicting types for 'kvm_get_fpu'
kvmctl.h:239: error: previous declaration of 'kvm_get_fpu' was here
kvmctl.c:538: error: conflicting types for 'kvm_get_fpu'
kvmctl.h:239: error: previous declaration of 'kvm_get_fpu' was here
kvmctl.c: In function `kvm_get_fpu':
kvmctl.c:539: error: `KVM_GET_FPU' undeclared (first use in this function)
kvmctl.c: At top level:
kvmctl.c:542: warning: "struct kvm_fpu" declared inside parameter list
kvmctl.c:543: error: conflicting types for 'kvm_set_fpu'
kvmctl.h:253: error: previous declaration of 'kvm_set_fpu' was here
kvmctl.c:543: error: conflicting types for 'kvm_set_fpu'
kvmctl.h:253: error: previous declaration of 'kvm_set_fpu' was here
kvmctl.c: In function `kvm_set_fpu':
kvmctl.c:544: error: `KVM_SET_FPU' undeclared (first use in this function)
kvmctl.c: In function `kvm_run_abi10':
kvmctl.c:903: error: `KVM_EXIT_FAIL_ENTRY' undeclared (first use in this function)
kvmctl.c: In function `kvm_run':
kvmctl.c:980: error: `KVM_EXIT_FAIL_ENTRY' undeclared (first use in this function)
kvmctl.c:982: error: structure has no member named `fail_entry'
kvmctl.c: At top level:
kvmctl.c:1037: warning: "struct kvm_cpuid_entry" declared inside parameter list
kvmctl.c:1038: error: conflicting types for 'kvm_setup_cpuid'
kvmctl.h:318: error: previous declaration of 'kvm_setup_cpuid' was here
kvmctl.c:1038: error: conflicting types for 'kvm_setup_cpuid'
kvmctl.h:318: error: previous declaration of 'kvm_setup_cpuid' was here
kvmctl.c: In function `kvm_setup_cpuid':
kvmctl.c:1042: error: dereferencing pointer to incomplete type
kvmctl.c:1042: error: dereferencing pointer to incomplete type
kvmctl.c:1046: error: dereferencing pointer to incomplete type
kvmctl.c:1047: error: dereferencing pointer to incomplete type
kvmctl.c:1047: error: dereferencing pointer to incomplete type
kvmctl.c:1048: error: `KVM_SET_CPUID' undeclared (first use in this function)
kvmctl.c: In function `kvm_set_signal_mask':
kvmctl.c:1060: error: `KVM_SET_SIGNAL_MASK' undeclared (first use in this function)
kvmctl.c:1065: error: dereferencing pointer to incomplete type
kvmctl.c:1069: error: dereferencing pointer to incomplete type
kvmctl.c:1070: error: dereferencing pointer to incomplete type
make[1]: *** [kvmctl.o] Error 1
make[1]: Leaving directory `/home/jacknn/kvm-35/user'
make: *** [user] Error 2

```

I'd like to:understand what's causing the failure, and whether I can get around it.

One thing 'make' complains about is kernel and userspace mismatch.

Does that mean I need another kernel to compile this KVM release?

Has anyone tried this compile? Can it be done in Feisty as is?

Thanks,
jackn

Ha

---

### Post by shad0w_walker on 2007-08-16
The KVM modules are included in feisty. You don't need to compile anything. Just modprobe kvm-amd or kvm-intel

---

### Post by jackn on 2007-08-16
Yes, I agree.

That's how I started. Using the built-in Feisty KVM went well until I tried to run some OS's. None ran. Feisty's KVM is release 16. The current KVM is release 35.

In any case, I'd like to try it.

The questions stand: 
What do the error messages tell me?
What can I do to 'make' release 35? 
Specifically, can it be done with Feisty's kernel?

Thanks, shas0w_walker.

jackn

---

### Post by relacksd on 2007-08-16
I assume that you configured your build with the --with-patched-kernel option. If you (re)configure without that option and then do your make of kvm-35, it should build (at least it does on my Feisty installation).

That said, I haven't found a clear explanation of the --with-patched-kernel option. I assume that it refers to building the kvm components either directly into the kernel or as modules (with the option indicating the former). If that assumption is right, then "make install" keeps everything clean in Feisty's /lib/modules directory and all is well (remember to use kvm-35's qemu tools and not those from the apt repositories).

I've had partial luck with kvm-35 on both an Intel and an AMD-based system. On one hand, my Linux virtual machines run beautifully. However, my Windows Server 2003 VM, which run fine on the stock Feisty install of KVM, crash on both Intel and AMD systems.

---

### Post by jackn on 2007-08-16
Now that's promising.

Yes, indeed, relacksed, I did use --wth-patched-kernel. And I'll try without this flag as soon as I have access to my box. Another instruction that I need to follow is to use KVM;s qemu tools and not the repo's. 
Having said that, I'm not sure what exactly it means to use KVM's qemu tools. Where is that?

As to the meaning of --with-patched-kernel, I don't know, you might be right. Before compiling, however, I had to understand it, as it was a fork in the [kvm wiki]("http://kvm.qumranet.com/kvmwiki/HOWTO")'s how to. 
One source for me was a gentoo howto which explained this about this flag:
> 
It's a reference to older kernels that didn't have KVM support included. New kernels ship with KVM, so they are patched, by definition. 

I therefore assumed that the feisty kernel was patched. My timorous bet would be that I was right, but that release 35 is not compatible with the 6.20 kernel, relying on more advanced versions thereof. So not using the --with-patched-kernel flag forces it to do what it would ideally let the kernel take care of.

---

### Post by jackn on 2007-08-17
OK, relacksed, no --with-patched-kernel worked very well. I went through the make and install without a snag.
Thank you for this tip.

For some reason, however, I only get the 64-bit version:
```
ls /usr/local/kvm/bin/
qemu-img  qemu-system-x86_64
```

According to the [KVM wiki]("http://kvm.qumranet.com/kvmwiki/HOWTO")'s how-to, I should also have plain 'qemu' there, used for 32-bit systems. Or perhaps I should only have the 32-bit version, by statting some option in the 'make' or 'config' step. This is not mentioned there.

Can you please help?

jackn

---

### Post by relacksd on 2007-08-24
> **jackn said:**
> OK, relacksed, no --with-patched-kernel worked very well. I went through the make and install without a snag.
Thank you for this tip.

For some reason, however, I only get the 64-bit version:
```
ls /usr/local/kvm/bin/
qemu-img  qemu-system-x86_64
```

According to the [KVM wiki]("http://kvm.qumranet.com/kvmwiki/HOWTO")'s how-to, I should also have plain 'qemu' there, used for 32-bit systems. Or perhaps I should only have the 32-bit version, by statting some option in the 'make' or 'config' step. This is not mentioned there.

Can you please help?

jackn

Glad to hear you got things compiled. A look at the Makefile reveals that qemu-system-x86_64 always gets built regardless of the bitness of your operating system. That said, I have built and run the resultant binary on both 32 bit and 64 bit versions of Feisty, so it doesn't seem to make any difference. Hopefully that is what you're finding as well.

In the interim I've got clarification on the --with-patched-kernel thing. Basically if you use that configure option, then you only build the qemu pieces of KVM and rely on the modules that come with the OS. If, however, you leave that option out, then both the qemu pieces and the KVM kernel modules are built. The Makefile is also smart enough to move the "old" modules out of the way.

Finally, just for the sake of completeness, I got Windows Server 2003 running on both Intel and AMD boxes. My original disk image never did work right, but on a clean reinstall everything is absolutely perfect.

There is now a kvm-36 release, but I gather there's a slight performance regression related to video and 32 bit Windows. Regardless, kvm-35 is working nicely for me and hopefully you, too.

---

