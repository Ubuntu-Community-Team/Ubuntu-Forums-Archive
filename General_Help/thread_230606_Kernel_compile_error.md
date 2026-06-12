---
title: "Kernel compile error"
date: 2006-08-06
forum: General Help
---

### Post by emil.s on 2006-08-06
What kernel makes no difference...

```
Sandnabba linux # make
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x493): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x6f2): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0x99e): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x1e0a): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o: In function `arch_ptrace':
(.text+0x499e): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:if.c:(.text+0x8a67): more undefined references to `__stack_chk_fail' follow
make: *** [.tmp_vmlinux1] Fel 1 
```
Fel 1 = Error 1

Anyone who know what the problem is?

---

### Post by Amaranth on 2006-08-06
Add -fno-stack-protector to the CFLAGS.

---

### Post by emil.s on 2006-08-06
> **Amaranth said:**
> Add -fno-stack-protector to the CFLAGS.

CFLAGS?
What is that? How did i use it?

---

### Post by trafiq on 2006-08-06
sudo gedit /usr/src/linux/Makefile

find line

CFLAGS 		:= -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

and change it to 

CFLAGS 		:= -fno-stack-protector -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

And be happy ;)

---

### Post by OBELIKS on 2006-08-20
Hi!
Hope you don't mind if I borrow this thread.
When i use make oldconfig the command goes through, but when I use make menuconfig I get the following error:
```
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:31:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:128: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âuse_colorsâ
scripts/kconfig/lxdialog/dialog.h:129: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âuse_shadowâ
scripts/kconfig/lxdialog/dialog.h:131: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âattributesâ
scripts/kconfig/lxdialog/dialog.h:143: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:146: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:147: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:148: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:149: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:151: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:31: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:59: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:95: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c: In function âdialog_checklistâ:
scripts/kconfig/lxdialog/checklist.c:117: error: âWINDOWâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:117: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:117: error: âdialogâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: âlistâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:117: warning: statement with no effect
scripts/kconfig/lxdialog/checklist.c:121: warning: implicit declaration of function âendwinâ
scripts/kconfig/lxdialog/checklist.c:122: warning: implicit declaration of function âfprintfâ
scripts/kconfig/lxdialog/checklist.c:122: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/kconfig/lxdialog/checklist.c:122: error: âstderrâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: error: âCOLSâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:141: error: âLINESâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function âdraw_shadowâ
scripts/kconfig/lxdialog/checklist.c:143: error: âstdscrâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ânewwinâ
scripts/kconfig/lxdialog/checklist.c:146: warning: implicit declaration of function âkeypadâ
scripts/kconfig/lxdialog/checklist.c:146: error: âTRUEâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function âdraw_boxâ
scripts/kconfig/lxdialog/checklist.c:148: error: âattributesâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:149: warning: implicit declaration of function âwattrsetâ
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function âmvwaddchâ
scripts/kconfig/lxdialog/checklist.c:152: warning: implicit declaration of function âwaddchâ
scripts/kconfig/lxdialog/checklist.c:156: warning: implicit declaration of function âprint_titleâ
scripts/kconfig/lxdialog/checklist.c:159: warning: implicit declaration of function âprint_autowrapâ
scripts/kconfig/lxdialog/checklist.c:166: warning: implicit declaration of function âsubwinâ
scripts/kconfig/lxdialog/checklist.c:190: warning: implicit declaration of function âprint_itemâ
scripts/kconfig/lxdialog/checklist.c:194: warning: implicit declaration of function âprint_arrowsâ
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function âprint_buttonsâ
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function âwnoutrefreshâ
scripts/kconfig/lxdialog/checklist.c:201: warning: implicit declaration of function âdoupdateâ
scripts/kconfig/lxdialog/checklist.c:204: warning: implicit declaration of function âwgetchâ
scripts/kconfig/lxdialog/checklist.c:211: error: âKEY_UPâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:211: error: âKEY_DOWNâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: error: âFALSEâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function âscrollokâ
scripts/kconfig/lxdialog/checklist.c:223: warning: implicit declaration of function âwscrlâ
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function âwrefreshâ
scripts/kconfig/lxdialog/checklist.c:282: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/kconfig/lxdialog/checklist.c:283: warning: implicit declaration of function âdelwinâ
scripts/kconfig/lxdialog/checklist.c:287: error: âKEY_LEFTâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:288: error: âKEY_RIGHTâ undeclared (first use in this function)
make[2]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

```
I'm using linux-source-2.6.17 from ubuntu repositories.

---

### Post by isharra on 2006-08-20
install ncurses-dev before using 'make menuconfig', you're missing headers and library that it needs.

---

### Post by OBELIKS on 2006-08-20
Thanks! I hope I can get the wireless to work finally.

---

### Post by ashrack on 2006-11-13
On EDGY final this bug still exists!
Any1 knows why it still hasn't been fixed?

---

### Post by ashrack on 2006-11-19
anyone?

---

### Post by Amaranth on 2006-11-19
Uh, it's not a bug. And I already said how to make the compile work.

---

### Post by ashrack on 2006-11-19
AMARANTH
So in EDGY I will also have to add those lines to compile NON UBUNTU kernels? 
Is their any permanent way of doing this? So I won't have to always add that line?

---

### Post by Amaranth on 2006-11-19
Yes, you need it for all kernels because they (obviously) don't use glibc. I don't know of any permanent place to put that, no. [Stack smashing protection](http://en.wikipedia.org/wiki/Stack-smashing_protection) is important enough that it's worth living with having to do little things like this.

---

### Post by ashrack on 2006-11-19
So that STACK is some kind of new protection! But Im still curious why with EDGY kernel I dont have to type that line but with the VANILLA kernel I must?
And also in DAPPER even with the VANILLA I didn't have to type that line! 
Please help me understand

---

### Post by Amaranth on 2006-11-19
edgy's kernel package has -fno-stack-protector and dapper didn't have this feature.

---

### Post by ashrack on 2006-11-20
aha, and thus it errors out when compiling VANILA kernel since they don't have -FNO-STACK-PROTECTOR, correct?
So, if this is true, is GCC then responsible for this behaviour? Have UBUNTU DEV patched it this way that it errors out on non -FNO-STACK-PROTECTOR kernels?

---

### Post by Amaranth on 2006-11-20
It's a stock GCC option but it's an Ubuntu thing to have it on by default.

---

### Post by nicolasgoddone on 2007-03-05
> **trafiq said:**
> sudo gedit /usr/src/linux/Makefile

find line

CFLAGS 		:= -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

and change it to 

CFLAGS 		:= -fno-stack-protector -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

And be happy ;)

Happy Indeed!....will make a toast for the tip tonight! thanx

---

### Post by H.E. Pennypacker on 2007-05-10
> **trafiq said:**
> sudo gedit /usr/src/linux/Makefile

find line

CFLAGS 		:= -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

and change it to 

CFLAGS 		:= -fno-stack-protector -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
	  	   -fno-strict-aliasing -fno-common

And be happy ;)

Thanks!

---

