---
title: "New Kernel released?  2.6.22?"
date: 2007-07-08
forum: General Help
---

### Post by Wes.Green on 2007-07-08
Ok so I read that a new Kernel has been release, apparently version 2.6.22 
[http://kernelnewbies.org/Linux_2_6_22#head-c3a33306c1f3f3f7f80a0e0dac70f75729134053]("http://kernelnewbies.org/Linux_2_6_22#head-c3a33306c1f3f3f7f80a0e0dac70f75729134053")

Now, I see theres some really awsome stuff here, specifically the wireless drivers support.  But I have no clue (newbie to linux) how to install this.  Please tell me its something thats pre-compiled so i can just run a file or something and it does it for me (wouldn't that be nice. lol)

Wireless is my main reason for wanting this, haven't been able to use my laptops wireless since I changed it to Ubuntu...

---

### Post by AlexThomson_NZ on 2007-07-08
Get the source from here:
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.tar.bz2)

Extract it and compile it.

I can't remember the commands exactly (it's been ages) but should be in the docs somewhere (it's like 4 lines or so).  It's actually very easy though, even for a newbie as because it is the kernel it doesn't have really any dependencies which usually make building from source such a pain!

Also, you get to tweak it to your system, and get a buzz from knowing you compiled it yourself! :)

Give it a go...

---

### Post by Wes.Green on 2007-07-09
Ok I tried to use the instructions that are in the kernel you linked for me...but nothing seems to be happening.

First it says to do this one
> 
bzip2 -dc linux-2.6.XX.tar.bz2 | tar xvf -


Then this
> 
linux/scripts/patch-kernel linux

**Which gets me this**
wesside@wesside-laptop:~/linux-2.6.22$ linux/scripts/patch-kernel linux
bash: linux/scripts/patch-kernel: No such file or directory


Finally it says to do these 2
> 
cd linux
make mrproper

**Which gets me this**
wesside@wesside-laptop:~/linux-2.6.22$ cd linux
bash: cd: linux: No such file or directory
wesside@wesside-laptop:~/linux-2.6.22$ make mrproper
  CLEAN   scripts/basic
  CLEAN   scripts/kconfig
  CLEAN   include/config


Thats all it says to do....and I have no clue  if its working or what, cause nothing seems to have happened.

---

### Post by AlexThomson_NZ on 2007-07-09
Ok I downloaded the new kernel and had a poke around to refresh my memory (I couldn't find a nice step-by-step guide, although it is probably buried away in there somewhere), but a quick google found:
[http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html)

Which gave a nice step by step guide. (although if you use gnome, try make gconfig instead of make xconfig)

Tada!

---

### Post by Wes.Green on 2007-07-09
/sigh I must be an idiot

I got to step 4 
> root@wesside-laptop:/home/wesside/linux-2.6.22# make xconfig
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2
root@wesside-laptop:/home/wesside/linux-2.6.22#  

I have no freaking clue what thats suppose to mean...:mad:

---

### Post by AlexThomson_NZ on 2007-07-09
> **AlexThomson_NZ said:**
> Which gave a nice step by step guide. (**although if you use gnome, try make gconfig instead of make xconfig**)

Tada!

No drama, please re-read my post

---

### Post by marsbt on 2007-07-09
You can also use the [Ubuntu method](https://help.ubuntu.com/community/Kernel/Compile) to compile your own kernel though.

---

### Post by Wes.Green on 2007-07-09
I also tried the gconfig, same basic error message (before i posted again)

> root@wesside-laptop:/home/wesside/linux-2.6.22# make gconfig
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_gtkcheck', needed by `scripts/kconfig/gconf.o'.  Stop.
make: *** [gconfig] Error 2
root@wesside-laptop:/home/wesside/linux-2.6.22#    

---

### Post by AlexThomson_NZ on 2007-07-09
Ahhh my bad, seems it does need some gtk development files.

Instead of gconfig try make menuconfig

---

### Post by atlfalcons866 on 2007-07-09
wont the new kernel be included in the updates?

---

### Post by AlexThomson_NZ on 2007-07-09
> **atlfalcons866 said:**
> wont the new kernel be included in the updates?

More than likely- but where's the fun in that! :)

---

### Post by pistcivet on 2007-07-09
I found this book to be very helpful when building my own kernel.
"Linux Kernel in a Nutshell" by Greg Kroah-Hartman.

Free and legal download:
[http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)

I had to rebuild the Zenwalk kernel to get support for an ISA soundcard.

---

### Post by Wes.Green on 2007-07-10
> root@wesside-laptop:/home/wesside/linux-2.6.22# make menuconfig
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
root@wesside-laptop:/home/wesside/linux-2.6.22#  

This doesnt look good in the least o.O  maybe i broke it heh

---

### Post by jocko on 2007-07-10
Why not try it the proper way: the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+master")

---

### Post by Wes.Green on 2007-07-19
Ok I got the new kernel installed, thanks for that link Jocko.

Now I'm running into the same problem I had before I installed the new kernel, my bcm4311 wireless still isn't recognized, even though it says that this kernel supports it.  

Any Ideas?:guitar:

---

### Post by Ayuthia on 2007-07-19
Gutsy comes with 2.6.22 and my 4311 did not start up out of the box.  Here is a link to some info about the 2.6.22 release.  If you search for 4311 you will see that a couple of people with 4311 cards have gotten it working but it looks like you might have to change some of your wireless configurations and possibly add some firmware.

[http://www4.osnews.com/comments/18228](http://www4.osnews.com/comments/18228)

---

