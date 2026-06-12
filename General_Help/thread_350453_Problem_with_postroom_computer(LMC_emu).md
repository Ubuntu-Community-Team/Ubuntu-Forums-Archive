---
title: "Problem with postroom computer(LMC emu)"
date: 2007-01-31
forum: General Help
---

### Post by Ademon on 2007-01-31
Hello all,

I am a 1st year student of Computing science and for one assignment i must work with an LMC(little man computer) emulator called "The postroom computer".

more information about postroom computer can be found here[http://scom.hud.ac.uk/scomhro/Courses/PostroomComputer/PostroomComputers/PostroomComputer7/body.html]("http://scom.hud.ac.uk/scomhro/Courses/PostroomComputer/PostroomComputers/PostroomComputer7/body.html")

For compiling i am using C++ compiler found in packet build-essential.

I have downloaded  PC.tar.gz (Postroom computer) and followed the instructions for compiling


```
 system("xtpanel - file /usr/local/bin/PC/xtpc.xts -file __xtpc.tmp\n");
```
with
```
 system("xtpanel - file /home/acheron/pc/PC/xtpc.xts -file __xtpc.tmp\n");
```
and compiled normally. After the compiling i get three executables and files with the extension *.o(propably examples of postroom computer?),

During the installation i am getting these messages that i am unable to identify:

```
acheron@acheron-laptop:~$ cd /home/acheron/PC
acheron@acheron-laptop:~/PC$ make pc
gcc -g -IH -IG -IX -I- -c C/Share/alloc.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Share/alloc.c: In function ‘memory_error’:
C/Share/alloc.c:9: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -g -IH -IG -IX -I- -c C/Share/drctve.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Share/drctve.c: In function ‘flags’:
C/Share/drctve.c:246: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/drctve.c:246: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/drctve.c:249: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/drctve.c:249: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -c C/Share/constant.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Share/errors.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Share/errors.c: In function ‘report_parse_error’:
C/Share/errors.c:52: warning: incompatible implicit declaration of built-in function ‘exit’
C/Share/errors.c:60: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -g -IH -IG -IX -I- -c C/Share/files.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Share/global.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Share/env.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Share/env.c: In function ‘preproc’:
C/Share/env.c:44: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/env.c: In function ‘preproc_env’:
C/Share/env.c:116: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/env.c:138: warning: incompatible implicit declaration of built-in function ‘exit’
C/Share/env.c: In function ‘preproc_input’:
C/Share/env.c:309: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -g -IH -IG -IX -I- -c C/Share/messages.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Share/words.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Share/tokens.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Share/tokens.c: In function ‘write_token’:
C/Share/tokens.c:175: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:184: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c: In function ‘const_t’:
C/Share/tokens.c:308: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:308: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c:319: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:319: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c: In function ‘var_t’:
C/Share/tokens.c:336: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:336: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c:343: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:343: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c: In function ‘comment_t’:
C/Share/tokens.c:363: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:363: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c:373: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:373: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Share/tokens.c: In function ‘string_t’:
C/Share/tokens.c:607: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Share/tokens.c:607: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -c C/Loadr/micro.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/op_table.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/mem.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Loadr/mem.c: In function ‘append_comment’:
C/Loadr/mem.c:169: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/mem.c:169: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -c C/Loadr/io_mod.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/cpu.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/intrrpt.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/alu.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/pcu.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Loadr/pcu.c: In function ‘fe_cycle’:
C/Loadr/pcu.c:293: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -g -IH -IG -IX -I- -c C/Loadr/pcparse.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Loadr/pcprint.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Loadr/pcprint.c: In function ‘print_source’:
C/Loadr/pcprint.c:36: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/pcprint.c: In function ‘print_error’:
C/Loadr/pcprint.c:84: warning: incompatible implicit declaration of built-in function ‘strlen’
make: *** No rule to make target `system.o', needed by `pc'. Stop.
```

```
acheron@acheron-laptop:~/PC$ make pca
gcc -g -IH -IG -IX -I- -c C/Assmb/object.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Assmb/print.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Assmb/print.c: In function ‘print_source’:
C/Assmb/print.c:49: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Assmb/print.c: In function ‘print_error’:
C/Assmb/print.c:97: warning: incompatible implicit declaration of built-in function ‘strlen’
gcc -g -IH -IG -IX -I- -c C/Assmb/expand.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Assmb/immdte.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Assmb/immdte.c: In function ‘code_list_from_string’:
C/Assmb/immdte.c:160: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Assmb/immdte.c:160: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Assmb/immdte.c:165: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Assmb/immdte.c:165: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -c C/Assmb/labels.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Assmb/link.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Assmb/clone.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/Assmb/parse.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c C/pca.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/pca.c: In function ‘main’:
C/pca.c:110: warning: incompatible implicit declaration of built-in function ‘strlen’
C/pca.c:110: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -o pca alloc.o drctve.o constant.o errors.o files.o global.o env.o messages.o words.o tokens.o object.o print.o expand.o immdte.o labels.o link.o clone.o parse.o  pca.o
```
```

acheron@acheron-laptop:~/PC$ make xtpanel.o
gcc -g -IH -IG -IX -I- -c -D XTPANEL C/System/XTpanel/system.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -c -D XTPANEL C/Loadr/lmc_io.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/Loadr/lmc_io.c: In function ‘init_trace_loc_expr’:
C/Loadr/lmc_io.c:321: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c: In function ‘init_trace_files’:
C/Loadr/lmc_io.c:338: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c: In function ‘lmc_pause’:
C/Loadr/lmc_io.c:444: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/lmc_io.c:444: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c:459: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/lmc_io.c:459: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c: In function ‘update_symb’:
C/Loadr/lmc_io.c:505: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/lmc_io.c:506: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c:508: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c: In function ‘pc_trace’:
C/Loadr/lmc_io.c:863: warning: incompatible implicit declaration of built-in function ‘strlen’
C/Loadr/lmc_io.c:868: warning: incompatible implicit declaration of built-in function ‘strcpy’
C/Loadr/lmc_io.c:905: warning: incompatible implicit declaration of built-in function ‘strcpy’
touch xtpanel.o

acheron@acheron-laptop:~/PC$ make xtpc
gcc -g -IH -IG -IX -I- -c C/pc.c
cc1: note: obsolete option -I- used, please use -iquote instead
C/pc.c: In function ‘main’:
C/pc.c:106: warning: incompatible implicit declaration of built-in function ‘strlen’
C/pc.c:106: warning: incompatible implicit declaration of built-in function ‘strcpy’
gcc -g -IH -IG -IX -I- -o pc alloc.o drctve.o constant.o errors.o files.o global.o env.o messages.o words.o tokens.o micro.o op_table.o mem.o io_mod.o cpu.o intrrpt.o alu.o pcu.o pcparse.o pcprint.o  system.o lmc_io.o pc.o
gcc -g -IH -IG -IX -I- -c -o xtpc-starter.o xtpc-starter.c
cc1: note: obsolete option -I- used, please use -iquote instead
gcc -g -IH -IG -IX -I- -o xtpc xtpc-starter.o
mv pc pc-xt
rm pc.o
acheron@acheron-laptop:~/PC$ acheron@acheron-laptop:~/PC$ ls
bash: acheron@acheron-laptop:~/PC$: No such file or directory
acheron@acheron-laptop:~/PC$ alloc.o     errors.o   io_mod.o    object.o    pc-xt      xtpc-starter.c
bash: alloc.o: command not found
acheron@acheron-laptop:~/PC$ alu.o       expand.o   labels.o    op_table.o  print.o    xtpc-starter.c~
bash: alu.o: command not found
acheron@acheron-laptop:~/PC$ C           files.o    link.o      parse.o     system.o   xtpc-starter.o
bash: C: command not found
acheron@acheron-laptop:~/PC$ clone.o     G          lmc_io.o    pca         tokens.o   xtpc.xts
bash: clone.o: command not found
acheron@acheron-laptop:~/PC$ constant.o  global.o   makefile    pca.o       words.o
bash: constant.o: command not found
acheron@acheron-laptop:~/PC$ cpu.o       H          mem.o       pcparse.o   X
bash: cpu.o: command not found
acheron@acheron-laptop:~/PC$ drctve.o    immdte.o   messages.o  pcprint.o   xtpanel.o
bash: drctve.o: command not found
acheron@acheron-laptop:~/PC$ env.o       intrrpt.o  micro.o     pcu.o       xtpc
bash: env.o: command not found
acheron@acheron-laptop:~/PC$
```

I also include an ls of my folder after the make process.
```
acheron@acheron-laptop:~/PC$ ls
alloc.o     errors.o   io_mod.o    object.o    pc-xt      xtpc-starter.c
alu.o       expand.o   labels.o    op_table.o  print.o    xtpc-starter.c~
C           files.o    link.o      parse.o     system.o   xtpc-starter.o
clone.o     G          lmc_io.o    pca         tokens.o   xtpc.xts
constant.o  global.o   makefile    pca.o       words.o
cpu.o       H          mem.o       pcparse.o   X
drctve.o    immdte.o   messages.o  pcprint.o   xtpanel.o
env.o       intrrpt.o  micro.o     pcu.o       xtpc
```

From what i have realized after doing a little research in order to run postroom computer under Linux i must use a dos emulator, i can use an emulator like dosbox or dosemu in order to run the postroom computer?

Please note that i am in an beginner maybe intermediate level of using linux.

Thank you in advantage.

---

