---
title: "help! Vim installation"
date: 2007-03-17
forum: General Help
---

### Post by kenyi25 on 2007-03-17
help, how do i compile vim properly??
Below are the errors occurred. :( 

> $ make
rm -f auto/config.status auto/config.cache config.log auto/config.log
rm -f auto/config.h auto/link.log auto/link.sed auto/config.mk
touch auto/config.h
cp config.mk.dist auto/config.mk
GUI_INC_LOC="" GUI_LIB_LOC="" \
                CC="" CPPFLAGS="" CFLAGS="" \
                LDFLAGS=""  srcdir="." \
                ./configure    \
                  \
                  \
                  \
                  \
                  \
                    \
                 
configure: creating cache auto/config.cache
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make -f Makefile all
make[1]: Entering directory `/home/kenyi/vim/vim70/src'
CC=" -Iproto            " srcdir=. sh ./osdef.sh
./osdef.sh: 54: -Iproto: not found
  Hmm, sed is very pessimistic about your system header files.
  But it did not dump core -- strange! Let's continue carefully...
  If this fails, you may want to remove offending lines from osdef.h
  or try with an empty osdef.h file, if your compiler can do without
  function declarations.
c -I. -Iproto              -o objects/buffer.o buffer.c
make[1]: c: Command not found
make[1]: [objects/buffer.o] Error 127 (ignored)
c -I. -Iproto              -o objects/charset.o charset.c
make[1]: c: Command not found
make[1]: [objects/charset.o] Error 127 (ignored)
c -I. -Iproto              -o objects/diff.o diff.c
make[1]: c: Command not found
make[1]: [objects/diff.o] Error 127 (ignored)
c -I. -Iproto              -o objects/digraph.o digraph.c
make[1]: c: Command not found
make[1]: [objects/digraph.o] Error 127 (ignored)
c -I. -Iproto              -o objects/edit.o edit.c
make[1]: c: Command not found
make[1]: [objects/edit.o] Error 127 (ignored)
c -I. -Iproto              -o objects/eval.o eval.c
make[1]: c: Command not found
make[1]: [objects/eval.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ex_cmds.o ex_cmds.c
make[1]: c: Command not found
make[1]: [objects/ex_cmds.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ex_cmds2.o ex_cmds2.c
make[1]: c: Command not found
make[1]: [objects/ex_cmds2.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ex_docmd.o ex_docmd.c
make[1]: c: Command not found
make[1]: [objects/ex_docmd.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ex_eval.o ex_eval.c
make[1]: c: Command not found
make[1]: [objects/ex_eval.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ex_getln.o ex_getln.c
make[1]: c: Command not found
make[1]: [objects/ex_getln.o] Error 127 (ignored)
c -I. -Iproto              -o objects/fileio.o fileio.c
make[1]: c: Command not found
make[1]: [objects/fileio.o] Error 127 (ignored)
c -I. -Iproto              -o objects/fold.o fold.c
make[1]: c: Command not found
make[1]: [objects/fold.o] Error 127 (ignored)
c -I. -Iproto              -o objects/getchar.o getchar.c
make[1]: c: Command not found
make[1]: [objects/getchar.o] Error 127 (ignored)
c -I. -Iproto              -o objects/hardcopy.o hardcopy.c
make[1]: c: Command not found
make[1]: [objects/hardcopy.o] Error 127 (ignored)
c -I. -Iproto              -o objects/hashtab.o hashtab.c
make[1]: c: Command not found
make[1]: [objects/hashtab.o] Error 127 (ignored)
c -I. -Iproto              -o objects/if_cscope.o if_cscope.c
make[1]: c: Command not found
make[1]: [objects/if_cscope.o] Error 127 (ignored)
c -I. -Iproto              -o objects/if_xcmdsrv.o if_xcmdsrv.c
make[1]: c: Command not found
make[1]: [objects/if_xcmdsrv.o] Error 127 (ignored)
c -I. -Iproto              -o objects/main.o main.c
make[1]: c: Command not found
make[1]: [objects/main.o] Error 127 (ignored)
c -I. -Iproto              -o objects/mark.o mark.c
make[1]: c: Command not found
make[1]: [objects/mark.o] Error 127 (ignored)
c -I. -Iproto              -o objects/memfile.o memfile.c
make[1]: c: Command not found
make[1]: [objects/memfile.o] Error 127 (ignored)
c -I. -Iproto              -o objects/memline.o memline.c
make[1]: c: Command not found
make[1]: [objects/memline.o] Error 127 (ignored)
c -I. -Iproto              -o objects/menu.o menu.c
make[1]: c: Command not found
make[1]: [objects/menu.o] Error 127 (ignored)
c -I. -Iproto              -o objects/message.o message.c
make[1]: c: Command not found
make[1]: [objects/message.o] Error 127 (ignored)
c -I. -Iproto              -o objects/misc1.o misc1.c
make[1]: c: Command not found
make[1]: [objects/misc1.o] Error 127 (ignored)
c -I. -Iproto              -o objects/misc2.o misc2.c
make[1]: c: Command not found
make[1]: [objects/misc2.o] Error 127 (ignored)
c -I. -Iproto              -o objects/move.o move.c
make[1]: c: Command not found
make[1]: [objects/move.o] Error 127 (ignored)
c -I. -Iproto              -o objects/mbyte.o mbyte.c
make[1]: c: Command not found
make[1]: [objects/mbyte.o] Error 127 (ignored)
c -I. -Iproto              -o objects/normal.o normal.c
make[1]: c: Command not found
make[1]: [objects/normal.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ops.o ops.c
make[1]: c: Command not found
make[1]: [objects/ops.o] Error 127 (ignored)
c -I. -Iproto              -o objects/option.o option.c
make[1]: c: Command not found
make[1]: [objects/option.o] Error 127 (ignored)
c -I. -Iproto              -o objects/os_unix.o os_unix.c
make[1]: c: Command not found
make[1]: [objects/os_unix.o] Error 127 (ignored)
creating auto/pathdef.c
tr: missing operand
Try `tr --help' for more information.
make[1]: [auto/pathdef.c] Error 1 (ignored)
tr: missing operand
Try `tr --help' for more information.
make[1]: [auto/pathdef.c] Error 1 (ignored)
tr: missing operand
Try `tr --help' for more information.
make[1]: [auto/pathdef.c] Error 1 (ignored)
tr: missing operand
Try `tr --help' for more information.
make[1]: [auto/pathdef.c] Error 1 (ignored)
c -I. -Iproto              -o objects/pathdef.o auto/pathdef.c
make[1]: c: Command not found
make[1]: [objects/pathdef.o] Error 127 (ignored)
c -I. -Iproto              -o objects/popupmnu.o popupmnu.c
make[1]: c: Command not found
make[1]: [objects/popupmnu.o] Error 127 (ignored)
c -I. -Iproto              -o objects/quickfix.o quickfix.c
make[1]: c: Command not found
make[1]: [objects/quickfix.o] Error 127 (ignored)
c -I. -Iproto              -o objects/regexp.o regexp.c
make[1]: c: Command not found
make[1]: [objects/regexp.o] Error 127 (ignored)
c -I. -Iproto              -o objects/screen.o screen.c
make[1]: c: Command not found
make[1]: [objects/screen.o] Error 127 (ignored)
c -I. -Iproto              -o objects/search.o search.c
make[1]: c: Command not found
make[1]: [objects/search.o] Error 127 (ignored)
c -I. -Iproto              -o objects/spell.o spell.c
make[1]: c: Command not found
make[1]: [objects/spell.o] Error 127 (ignored)
c -I. -Iproto              -o objects/syntax.o syntax.c
make[1]: c: Command not found
make[1]: [objects/syntax.o] Error 127 (ignored)
c -I. -Iproto              -o objects/tag.o tag.c
make[1]: c: Command not found
make[1]: [objects/tag.o] Error 127 (ignored)
c -I. -Iproto              -o objects/term.o term.c
make[1]: c: Command not found
make[1]: [objects/term.o] Error 127 (ignored)
c -I. -Iproto              -o objects/ui.o ui.c
make[1]: c: Command not found
make[1]: [objects/ui.o] Error 127 (ignored)
c -I. -Iproto              -o objects/undo.o undo.c
make[1]: c: Command not found
make[1]: [objects/undo.o] Error 127 (ignored)
c -I. -Iproto              -o objects/window.o window.c
make[1]: c: Command not found
make[1]: [objects/window.o] Error 127 (ignored)

---

### Post by lloyd_b on 2007-03-17
The first question: why build vim the hard way?  A limited version (vim-tiny) is installed by default, and you can install more complete versions (vim, vim-full) from the repositories.

Second:
> ```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```
```
CC=" -Iproto " srcdir=. sh ./osdef.sh
./osdef.sh: 54: -Iproto: not found
Hmm, sed is very pessimistic about your system header files.
But it did not dump core -- strange! Let's continue carefully...
```
These are indications that there are problems with the compiler and/or header files on your computer.  I would suggest installing the package "build-essential", as it contains pretty much everything you need for a working build system.

Lloyd B.

---

### Post by kenyi25 on 2007-03-17
Thnx lloyd_b,
by the way how do I launch the vim-tiny?? :confused:

---

### Post by lloyd_b on 2007-03-17
In a terminal window, just type "vi {filename}" - "vi" is symlinked to "vim-tiny".  Note that a lot of vim's features, including syntax highlighting, is not available with vim-tiny - you need to install the "vim" or "vim-full" package to get that ("vim" is the full text-mode vim, vim-full includes the "gvim" graphical version for gnome).

Lloyd B.

---

