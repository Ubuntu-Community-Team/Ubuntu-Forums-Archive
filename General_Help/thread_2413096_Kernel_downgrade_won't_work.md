---
title: "Kernel downgrade won't work"
date: 2019-02-21
forum: General Help
---

### Post by butinbutout on 2019-02-21
Hi,

I am running Ubuntu 16.04 with kernel 4.15 and I need to downgrade to a kernel version of 3.2.
I downloaded several 3.2.X kernels from [https://launchpad.net/linux/3.2](https://launchpad.net/linux/3.2) and followed the installation guide according to [https://launchpad.net/linux/3.2](https://launchpad.net/linux/3.2) specifically:

- I extract the .tar.gz
- ```
make menuconfig
``` followed by save and exit
- Make dependencies ```
[COLOR=#000000]make dep[/COLOR]
```
- This is where it goes wrong, with the following errors: ```
make modules
```

```
make[1]: Nothing to be done for 'relocs'.  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CALL    scripts/checksyscalls.sh
  CC [M]  arch/x86/kvm/svm.o
arch/x86/kvm/svm.c: In function &#8216;svm_vcpu_run&#8217;:
arch/x86/kvm/svm.c:3707:18: error: invalid character ' ' in raw string delimiter
   "push %%"R"bp; \n\t"
                  ^
arch/x86/kvm/svm.c:3707:3: error: stray &#8216;R&#8217; in program
   "push %%"R"bp; \n\t"
   ^
arch/x86/kvm/svm.c:3708:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rbx](%[svm]), %%"R"bx \n\t"
                                 ^
arch/x86/kvm/svm.c:3707:13: error: expected &#8216;:&#8217; or &#8216;)&#8217; before string constant
   "push %%"R"bp; \n\t"
             ^
arch/x86/kvm/svm.c:3707:13: error: stray &#8216;R&#8217; in program
arch/x86/kvm/svm.c:3709:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rcx](%[svm]), %%"R"cx \n\t"
                                 ^
arch/x86/kvm/svm.c:3709:3: error: stray &#8216;R&#8217; in program
   "mov %c[rcx](%[svm]), %%"R"cx \n\t"
   ^
arch/x86/kvm/svm.c:3710:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rdx](%[svm]), %%"R"dx \n\t"
                                 ^
arch/x86/kvm/svm.c:3710:3: error: stray &#8216;R&#8217; in program
   "mov %c[rdx](%[svm]), %%"R"dx \n\t"
   ^
arch/x86/kvm/svm.c:3711:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rsi](%[svm]), %%"R"si \n\t"
                                 ^
arch/x86/kvm/svm.c:3711:3: error: stray &#8216;R&#8217; in program
   "mov %c[rsi](%[svm]), %%"R"si \n\t"
   ^
arch/x86/kvm/svm.c:3712:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rdi](%[svm]), %%"R"di \n\t"
                                 ^
arch/x86/kvm/svm.c:3712:3: error: stray &#8216;R&#8217; in program
   "mov %c[rdi](%[svm]), %%"R"di \n\t"
   ^
arch/x86/kvm/svm.c:3713:33: error: invalid character ' ' in raw string delimiter
   "mov %c[rbp](%[svm]), %%"R"bp \n\t"
                                 ^
arch/x86/kvm/svm.c:3713:3: error: stray &#8216;R&#8217; in program
   "mov %c[rbp](%[svm]), %%"R"bp \n\t"
   ^
arch/x86/kvm/svm.c:3726:17: error: invalid character ' ' in raw string delimiter
   "push %%"R"ax \n\t"
                 ^
arch/x86/kvm/svm.c:3726:3: error: stray &#8216;R&#8217; in program
   "push %%"R"ax \n\t"
   ^
arch/x86/kvm/svm.c:3727:34: error: invalid character ' ' in raw string delimiter
   "mov %c[vmcb](%[svm]), %%"R"ax \n\t"
                                  ^
arch/x86/kvm/svm.c:3727:3: error: stray &#8216;R&#8217; in program
   "mov %c[vmcb](%[svm]), %%"R"ax \n\t"
   ^
arch/x86/kvm/svm.c:3731:16: error: invalid character ' ' in raw string delimiter
   "pop %%"R"ax \n\t"
                ^
arch/x86/kvm/svm.c:3731:3: error: stray &#8216;R&#8217; in program
   "pop %%"R"ax \n\t"
   ^
arch/x86/kvm/svm.c:3734:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"bx, %c[rbx](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3734:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"bx, %c[rbx](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3735:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"cx, %c[rcx](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3735:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"cx, %c[rcx](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3736:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"dx, %c[rdx](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3736:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"dx, %c[rdx](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3737:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"si, %c[rsi](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3737:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"si, %c[rsi](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3738:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"di, %c[rdi](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3738:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"di, %c[rdi](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3739:17: error: invalid character ' ' in raw string delimiter
   "mov %%"R"bp, %c[rbp](%[svm]) \n\t"
                 ^
arch/x86/kvm/svm.c:3739:3: error: stray &#8216;R&#8217; in program
   "mov %%"R"bp, %c[rbp](%[svm]) \n\t"
   ^
arch/x86/kvm/svm.c:3750:17: error: invalid new-line in raw string delimiter
arch/x86/kvm/svm.c:3750:3: error: stray &#8216;R&#8217; in program
   "pop %%"R"bp"
   ^
arch/x86/kvm/svm.c:3771:12: error: invalid character ' ' in raw string delimiter
   , R"bx", R"cx", R"dx", R"si", R"di"
            ^
arch/x86/kvm/svm.c:3771:3: error: stray &#8216;R&#8217; in program
   , R"bx", R"cx", R"dx", R"si", R"di"
   ^
arch/x86/kvm/svm.c:3771:19: error: invalid character ' ' in raw string delimiter
   , R"bx", R"cx", R"dx", R"si", R"di"
                   ^
arch/x86/kvm/svm.c:3771:3: error: stray &#8216;R&#8217; in program
   , R"bx", R"cx", R"dx", R"si", R"di"
   ^
arch/x86/kvm/svm.c:3771:26: error: invalid character ' ' in raw string delimiter
   , R"bx", R"cx", R"dx", R"si", R"di"
                          ^
arch/x86/kvm/svm.c:3771:3: error: stray &#8216;R&#8217; in program
   , R"bx", R"cx", R"dx", R"si", R"di"
   ^
arch/x86/kvm/svm.c:3771:33: error: invalid character ' ' in raw string delimiter
   , R"bx", R"cx", R"dx", R"si", R"di"
                                 ^
arch/x86/kvm/svm.c:3771:3: error: stray &#8216;R&#8217; in program
   , R"bx", R"cx", R"dx", R"si", R"di"
   ^
arch/x86/kvm/svm.c:3771:39: error: invalid new-line in raw string delimiter
arch/x86/kvm/svm.c:3771:3: error: stray &#8216;R&#8217; in program
   , R"bx", R"cx", R"dx", R"si", R"di"
   ^
scripts/Makefile.build:305: recipe for target 'arch/x86/kvm/svm.o' failed
make[2]: *** [arch/x86/kvm/svm.o] Error 1
scripts/Makefile.build:441: recipe for target 'arch/x86/kvm' failed
make[1]: *** [arch/x86/kvm] Error 2
Makefile:947: recipe for target 'arch/x86' failed
make: *** [arch/x86] Error 2
```

This fault has occurred for several attempts with different kernel versions (3.2.X).
Any help is appreciated!

---

