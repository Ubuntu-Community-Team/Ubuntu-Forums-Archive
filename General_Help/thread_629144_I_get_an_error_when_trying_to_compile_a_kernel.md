---
title: "I get an error when trying to compile a kernel"
date: 2007-12-02
forum: General Help
---

### Post by PmDematagoda on 2007-12-02
When I try to use:-

```
make bzImage
```

I get the following error:-

```
kernel/sys.c: In function ‘set_user’:
kernel/sys.c:1087: error: dereferencing pointer to incomplete type
make[1]: *** [kernel/sys.o] Error 1
make: *** [kernel] Error 2

```

I would greatly appreciate any help concerning this matter.

P.S. For anyone wondering, I have used Kernel Check before and know what it is for, so don't waste your time trying to tell me all about Kernel Check:).

---

### Post by elctb on 2007-12-02
The kernel almost always compiles, specially the kernel/sys.c file. Most compile errors are on unmaintained drivers. Therefore, the problem might be a configuration issue.

Save your kernel configuration file. Then do the following:

```
make mrproper
make menuconfig
make bzImage
``` 

The "make menuconfig" step might take a while. You can get a default configuration file from the arch/<your-cpu>/configs directory.

---

### Post by PmDematagoda on 2007-12-02
The problem still remains:(.

```
kernel/sys.c: In function &#8216;set_user&#8217;:
kernel/sys.c:1087: error: dereferencing pointer to incomplete type
make[1]: *** [kernel/sys.o] Error 1
make: *** [kernel] Error 2

```

EDIT:- The problem remains but it does manage to complete the process a little more than last time.

---

### Post by elctb on 2007-12-02
Open kernel/sys.c go to line 1087 and post it here.

Also, what kernel version are you compiling ? Is it a kernel from kernel.org or some third party kernel ?

Let us know what default config file you are using, or post your custom config file.

---

### Post by PmDematagoda on 2007-12-03
The line 1087 is:-
```

			new_user != current->nsproxy->user_ns->root_user) {
```

I'm compiling Kernel 2.6.22 which I got from the Ubuntu repositories.

I cannot run make menu config for some reason, even with sudo, I get this message:-

 ```
 HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before ‘chtype’
scripts/kconfig/lxdialog/dialog.h:187: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:194: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:196: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:197: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:198: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:199: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:201: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:31: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:59: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:95: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c: In function ‘dialog_checklist’:
scripts/kconfig/lxdialog/checklist.c:116: error: ‘WINDOW’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘list’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function ‘getmaxy’
scripts/kconfig/lxdialog/checklist.c:129: error: ‘stdscr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: ‘KEY_MAX’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function ‘getmaxx’
scripts/kconfig/lxdialog/checklist.c:137: error: ‘COLS’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: ‘LINES’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function ‘draw_shadow’
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function ‘newwin’
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function ‘keypad’
scripts/kconfig/lxdialog/checklist.c:143: error: ‘TRUE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ‘draw_box’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function ‘wattrset’
scripts/kconfig/lxdialog/checklist.c:147: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function ‘mvwaddch’
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function ‘waddch’
scripts/kconfig/lxdialog/checklist.c:151: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function ‘print_title’
scripts/kconfig/lxdialog/checklist.c:156: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function ‘print_autowrap’
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function ‘subwin’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function ‘print_item’
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function ‘print_arrows’
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function ‘print_buttons’
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function ‘wnoutrefresh’
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function ‘doupdate’
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function ‘wgetch’
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_UP’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_DOWN’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: ‘FALSE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function ‘scrollok’
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function ‘wscrl’
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function ‘wrefresh’
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function ‘delwin’
scripts/kconfig/lxdialog/checklist.c:297: error: ‘KEY_LEFT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: ‘KEY_RIGHT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function ‘on_key_esc’
scripts/kconfig/lxdialog/checklist.c:312: error: ‘KEY_RESIZE’ undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

But I can make a config file using make config.

But when I try to make a .config file, I get an error saying:-
```

*** Error during writing of the kernel configuration.

make[1]: *** [config] Error 1
make: *** [config] Error 2

```

By the way, thanks a lot for the help elctb, I greatly appreciate it:).

---

### Post by elctb on 2007-12-03
It looks like you don't have the libncurses5-dev package. You must install it to make menuconfig

```
sudo apt-get install libncurses5-dev
```

Also, it looks like root owns the linux sources. Therefore, you need to use sudo to build config, menuconfig, bzImage, etc.

```
sudo make mrproper
sudo make menuconfig
sudo make bzImage
```

I'm not familiar with how ubuntu installs kernel sources. I've always gotten the kernel from kernel.org. If you still can't compile the kernel, I would suggest you download 2.6.22 (or if you prefer the latest kernel 2.6.23.9) from kernel.org and try again. After you untar the kernel sources and run "sudo make mrproper"
copy the /boot/config-<your-kernel> as .config. Run "sudo make oldconfig" and accept all the default values. Then just do "sudo make bzImage". Post any errors you get.

---

### Post by PmDematagoda on 2007-12-04
I downloaded the kernel source from Kernel.org but it still cannot run:-

```
sudo make menuconfig
```

And gives me these errors:-
```
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before ‘chtype’
scripts/kconfig/lxdialog/dialog.h:187: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:194: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:196: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:197: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:198: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:199: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:201: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:31: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:59: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:95: error: expected ‘)’ before ‘*’ token
scripts/kconfig/lxdialog/checklist.c: In function ‘dialog_checklist’:
scripts/kconfig/lxdialog/checklist.c:116: error: ‘WINDOW’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: ‘list’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function ‘getmaxy’
scripts/kconfig/lxdialog/checklist.c:129: error: ‘stdscr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: ‘KEY_MAX’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function ‘getmaxx’
scripts/kconfig/lxdialog/checklist.c:137: error: ‘COLS’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: ‘LINES’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function ‘draw_shadow’
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function ‘newwin’
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function ‘keypad’
scripts/kconfig/lxdialog/checklist.c:143: error: ‘TRUE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ‘draw_box’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function ‘wattrset’
scripts/kconfig/lxdialog/checklist.c:147: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function ‘mvwaddch’
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function ‘waddch’
scripts/kconfig/lxdialog/checklist.c:151: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function ‘print_title’
scripts/kconfig/lxdialog/checklist.c:156: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function ‘print_autowrap’
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function ‘subwin’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:171: error: ‘struct dialog_color’ has no member named ‘atr’
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function ‘print_item’
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function ‘print_arrows’
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function ‘print_buttons’
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function ‘wnoutrefresh’
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function ‘doupdate’
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function ‘wgetch’
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_UP’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: ‘KEY_DOWN’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: ‘FALSE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function ‘scrollok’
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function ‘wscrl’
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function ‘wrefresh’
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function ‘delwin’
scripts/kconfig/lxdialog/checklist.c:297: error: ‘KEY_LEFT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: ‘KEY_RIGHT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function ‘on_key_esc’
scripts/kconfig/lxdialog/checklist.c:312: error: ‘KEY_RESIZE’ undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

---

### Post by elctb on 2007-12-04
You need to install the ncurses library:

```
sudo apt-get install libncurses5-dev
```

---

### Post by PmDematagoda on 2007-12-07
Finally I managed to compile a kernel properly. Now I face a last stage problem, where do I find the initrd image for this kernel? I looked around yet I cannot find it.

---

### Post by elctb on 2007-12-07
You don't need the initrd if you built a bzImage.

Just keep the ubuntu kernel around until you're sure you don't need it. This is what my /boot/grub/menu.lst file looks like:

```
title           linux-2.6.23.1
root            (hd0,1)
kernel          /boot/bzImage-2.6.23.1 ro

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cad19e87-94d4-4874-a282-942f422f6784 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cad19e87-94d4-4874-a282-942f422f6784 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

```

---

