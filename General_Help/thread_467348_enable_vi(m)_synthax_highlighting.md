---
title: "enable vi(m) synthax highlighting"
date: 2007-06-07
forum: General Help
---

### Post by balki2005 on 2007-06-07
hello,

I tried  to  enable  synthax highlighting but without success, somebody know  how to resolve this ??

root@thunderdragon:/etc/vim# vim
Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version: syntax on
Press ENTER or type command to continue



VIM - Vi IMproved 7.0 (2006 May 7, compiled May 22 2007 21:10:57)
Included patches: 1-164, 234-235
Compiled by [email]buildd@rothera.buil[/email]dd
Small version without GUI.  Features included (+) or not (-):
-arabic +autocmd -balloon_eval -browse +builtin_terms +byte_offset -cindent 
-clientserver -clipboard +cmdline_compl +cmdline_hist +cmdline_info +comments 
-cryptv -cscope -cursorshape -dialog +diff +digraphs -dnd -ebcdic -emacs_tags 
+eval +ex_extra +extra_search -farsi +file_in_path -find_in_path +folding 
-footer +fork() -gettext -hangul_input +iconv +insert_expand +jumplist -keymap 
-langmap +libcall -linebreak -lispindent +listcmds -localmap -menu -mksession 
-modify_fname -mouse -mouse_dec -mouse_gpm -mouse_jsbterm -mouse_netterm 
-mouse_xterm +multi_byte -multi_lang -mzscheme -netbeans_intg -osfiletype 
-path_extra -perl -printer -profile -python +quickfix -reltime -rightleft -ruby
 +scrollbind -signs +smartindent -sniff -statusline -sun_workshop -syntax 
-tag_binary -tag_old_static -tag_any_white -tcl +terminfo -termresponse 
+textobjects -title -toolbar +user_commands +vertsplit -virtualedit +visual 
+visualextra +viminfo -vreplace +wildignore -wildmenu +windows +writebackup 
-X11 +xfontset -xim -xsmp -xterm_clipboard -xterm_save 
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
      user exrc file: "$HOME/.exrc"
  fall-back for $VIM: "/usr/share/vim"
Compilation: gcc -c -I. -Iproto -DHAVE_CONFIG_H     -O2 -g -Wall -DFEAT_AUTOCMD -DFEAT_BYTEOFF -DFEAT_CMDL_COMPL -DFEAT_CMDHIST -DFEAT_CMDL_INFO -DFEAT_COMMENTS -DFEAT_DIFF -DFEAT_DIGRAPHS -DFEAT_EVAL -DFEAT_EX_EXTRA -DFEAT_SEARCH_EXTRA -DFEAT_SEARCHPATH -DFEAT_FOLDING -DFEAT_INS_EXPAND -DFEAT_LISTCMDS -DFEAT_QUICKFIX -DFEAT_SCROLLBIND -DFEAT_SMARTINDENT -DFEAT_TEXTOBJ -DFEAT_USR_CMDS -DFEAT_VERTSPLIT -DFEAT_VIMINFO -DFEAT_VISUALEXTRA        
Linking: gcc   -L/usr/local/lib -o vim    -lncurses         
root@thunderdragon:/etc# 

I also tried  to create  a local  .vimrc but also  withoout success !!  :(

please help  !!

balki2005

---

### Post by rapolas on 2007-06-07
Go to synaptic and install vim;) I'm serious.. sudo apt-get install vim

---

### Post by agger on 2007-06-07
> **rapolas said:**
> Go to synaptic and install vim;) I'm serious.. sudo apt-get install vim

And after that, in vi(m) write 

```
:syntax on
```

You can also write the line "syntax on" to ~/.exrc

---

### Post by reclusivemonkey on 2007-06-07
Also, you shouldn't be running as root.

---

### Post by balki2005 on 2007-06-08
yep, I know !! but I was still  in root mode because modifying the vimrc file.

rgds,

balki2005

---

### Post by balki2005 on 2007-06-08
hello !! 

thanks  it works !!! I did  like  you  told:

sudo apt-get install vim


thanks  !!! 

balki2005

---

