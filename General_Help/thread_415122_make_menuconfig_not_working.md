---
title: "make menuconfig not working?"
date: 2007-04-20
forum: General Help
---

### Post by carlosqueso on 2007-04-20
When I use make menuconfig (as root), I get ```
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before âchtypeâ
scripts/kconfig/lxdialog/dialog.h:187: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:193: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:195: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:196: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:197: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:198: error: expected â)â before â*â token
scripts/kconfig/lxdialog/dialog.h:200: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:31: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:59: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c:95: error: expected â)â before â*â token
scripts/kconfig/lxdialog/checklist.c: In function âdialog_checklistâ:
scripts/kconfig/lxdialog/checklist.c:116: error: âWINDOWâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: âdialogâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: âlistâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function âgetmaxyâ
scripts/kconfig/lxdialog/checklist.c:129: error: âstdscrâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: âKEY_MAXâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function âgetmaxxâ
scripts/kconfig/lxdialog/checklist.c:137: error: âCOLSâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: âLINESâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function âdraw_shadowâ
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function ânewwinâ
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function âkeypadâ
scripts/kconfig/lxdialog/checklist.c:143: error: âTRUEâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function âdraw_boxâ
scripts/kconfig/lxdialog/checklist.c:146: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:146: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function âwattrsetâ
scripts/kconfig/lxdialog/checklist.c:147: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function âmvwaddchâ
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function âwaddchâ
scripts/kconfig/lxdialog/checklist.c:151: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function âprint_titleâ
scripts/kconfig/lxdialog/checklist.c:156: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function âprint_autowrapâ
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function âsubwinâ
scripts/kconfig/lxdialog/checklist.c:171: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:171: error: âstruct dialog_colorâ has no member named âatrâ
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function âprint_itemâ
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function âprint_arrowsâ
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function âprint_buttonsâ
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function âwnoutrefreshâ
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function âdoupdateâ
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function âwgetchâ
scripts/kconfig/lxdialog/checklist.c:210: error: âKEY_UPâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: âKEY_DOWNâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: âFALSEâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function âscrollokâ
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function âwscrlâ
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function âwrefreshâ
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function âdelwinâ
scripts/kconfig/lxdialog/checklist.c:297: error: âKEY_LEFTâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: âKEY_RIGHTâ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function âon_key_escâ
scripts/kconfig/lxdialog/checklist.c:312: error: âKEY_RESIZEâ undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

Bug, or did I forget to apt-get a required library?

---

### Post by carlosqueso on 2007-04-20
Never mind.....forgot libncurses5-dev:oops:

---

### Post by dogeatery on 2007-05-26
I am having this same problem with ndiswrapper!  Is there a dependency I need to install in Xubuntu Feisty?

---

### Post by dogeatery on 2007-05-26
:DI found all the dependencies for ndiswrapper, no problems!

---

