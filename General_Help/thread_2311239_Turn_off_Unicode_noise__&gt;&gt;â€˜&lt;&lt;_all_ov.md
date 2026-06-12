---
title: "Turn off Unicode noise  &gt;&gt;â€˜&lt;&lt; all over log files"
date: 2016-01-25
forum: General Help
---

### Post by brian117 on 2016-01-25
I just setup a new Ubuntu 15.10 development workstation to get some C code ported to Linux. 

When viewing gcc log files in Gvim from windoz, I am seeing unicode debris everywhere, each time I compile. Ex:
In function â€˜fill_raw_file_stat_strâ€™:

These extraneous strings are distracting   >>  â€™  <<  and  >> â€˜ <<

How do I simply and permanently remove all traces of unicode? 

I know that I can manually fix each occurrence with something like:
piconv -f UTF-16BE -t ascii      noisy.unicode.txt  >  clean.txt

I would rather not compile, >>â€™<<fix_unicode_noise>>â€˜<< and then read. I wish to turn off unicode entirely.

---

### Post by steeldriver on 2016-01-25
Hello and welcome to the forums

How exactly are you "viewing gcc log files in Gvim from windoz"? The behaviour you're describing looks like it's more to do with translation between character sets, rather than the original encodings themselves (for example, using putty's default ISO-8859 character set when the remote source is in fact UTF-8)

---

### Post by brian117 on 2016-01-25
I setup Samba (latest, source) and share the directory on Linux with windoz with Webmin.
I have only 1 good monitor so I need to share it between the workstations ;(
I use gvim on both the code and the compiler output (details below).
When I run duplicate file reports with CCleaner, I get similar results and the files are 2 (or 3?) times as large indicating multi-byte chars.
Once per blue moon when I spruce up the old hard drive, manually weeding one report is not too onerous.
With C code, compiling and editing every few minutes, fixing the comiler spew each time gets old

As as test, if I use vi through putty on windoz, the circumflex a (â) is everywhere

When I use vi in "Terminator" terminal in Ubuntu 15.10, single quotes show where the "â" or "â&#8364;&#732;" are showing up in windows
Doesn't this point to Ubuntu's file system internationalizing the output?

One more clue, I get 6700 "?" characters when I use this old CCleaner-report-fixing trick on the ~unicode Ubuntu log file saved to windows with gvim->save_as
piconv -f UTF-16BE -t ascii gcc.unicode.log > gcc.ascii.log



windoz _vimrc:
---------------
set nocompatible
set bs=2
set backupdir=c:/temp/vim
set directory=c:/temp/vim
set shiftwidth=4
set tabstop=4
set visualbell
set autoindent
set cindent
set hlsearch
"set statusline=%m%r%h%w [H=%02.2B] [p=%04l,%04v][%p%%] [L=%l]
"set laststatus=2

source $VIMRUNTIME/vimrc_example.vim
source $VIMRUNTIME/mswin.vim
behave mswin

":let g:session_autosave = 'yes'
:let g:session_autoload = 'no'
:let g:session_autosave = 'no'


windoz gvim --version:
--------------------
VIM - Vi IMproved 7.3 (2010 Aug 15, compiled Oct 27 2010 17:59:02)
MS-Windows 32-bit GUI version with OLE support
Included patches: 1-46
Compiled by Bram@KIBAALE
Big version with GUI. Features included (+) or not (-):
+arabic +autocmd +balloon_eval +browse ++builtin_terms +byte_offset +cindent
+clientserver +clipboard +cmdline_compl +cmdline_hist +cmdline_info +comments
+conceal +cryptv +cscope +cursorbind +cursorshape +dialog_con_gui +diff
+digraphs -dnd -ebcdic +emacs_tags +eval +ex_extra +extra_search +farsi
+file_in_path +find_in_path +float +folding -footer +gettext/dyn -hangul_input
+iconv/dyn +insert_expand +jumplist +keymap +langmap +libcall +linebreak
+lispindent +listcmds +localmap -lua +menu +mksession +modify_fname +mouse
+mouseshape +multi_byte_ime/dyn +multi_lang -mzscheme +netbeans_intg +ole
-osfiletype +path_extra +perl/dyn +persistent_undo -postscript +printer
-profile +python/dyn +python3/dyn +quickfix +reltime +rightleft +ruby/dyn
+scrollbind +signs +smartindent -sniff +startuptime +statusline -sun_workshop
+syntax +tag_binary +tag_old_static -tag_any_white +tcl/dyn -tgetent
-termresponse +textobjects +title +toolbar +user_commands +vertsplit
+virtualedit +visual +visualextra +viminfo +vreplace +wildignore +wildmenu
+windows +writebackup -xfontset -xim -xterm_save +xpm_w32
system vimrc file: "$VIM\vimrc"
user vimrc file: "$HOME\_vimrc"
2nd user vimrc file: "$VIM\_vimrc"
user exrc file: "$HOME\_exrc"
2nd user exrc file: "$VIM\_exrc"
system gvimrc file: "$VIM\gvimrc"
user gvimrc file: "$HOME\_gvimrc"
2nd user gvimrc file: "$VIM\_gvimrc"
system menu file: "$VIMRUNTIME\menu.vim"
Compilation: cl -c /W3 /nologo -I. -Iproto -DHAVE_PATHDEF -DWIN32 -DFEAT_CSCOPE -DFEAT_NETBEANS_INTG
-DFEAT_XPM_W32 -DWINVER=0x0400 -D_WIN32_WINNT=0x0400 /Fo.\ObjGOLYHTR/ /Ox /GL -DNDEBUG /Zl /MT
-DFEAT_OLE -DFEAT_MBYTE_IME -DDYNAMIC_IME -DFEAT_GUI_W32 -DDYNAMIC_ICONV -DDYNAMIC_GETTEXT
-DFEAT_TCL -DDYNAMIC_TCL -DDYNAMIC_TCL_DLL=\"tcl83.dll\" -DDYNAMIC_TCL_VER=\"8.3\" -DFEAT_PYTHON
-DDYNAMIC_PYTHON -DDYNAMIC_PYTHON_DLL=\"python27.dll\" -DFEAT_PYTHON3 -DDYNAMIC_PYTHON3
-DDYNAMIC_PYTHON3_DLL=\"python31.dll\" -DFEAT_PERL -DDYNAMIC_PERL -DDYNAMIC_PERL_DLL=\"perl512.dll\"
-DFEAT_RUBY -DDYNAMIC_RUBY -DDYNAMIC_RUBY_VER=191 -DDYNAMIC_RUBY_DLL=\"msvcrt-ruby191.dll\" -DFEAT_BIG
/Fd.\ObjGOLYHTR/ /Zi
Linking: link /RELEASE /nologo /subsystem:windows /LTCG:STATUS oldnames.lib kernel32.lib advapi32.lib shell32.lib gdi32.lib

---

### Post by steeldriver on 2016-01-25
Have you tried executing

```

set encoding=utf-8

```

in vim?

---

### Post by brian117 on 2016-01-25
Just tried it on the same Putty window I am running gcc:
brianp@raptor:~/bin$  set encoding=utf-8
brianp@raptor:~/bin$ gcc -Wformat=0  -ffast-math -m64 -Ofast -march=native -fopenmp -funroll-loops -flto          /home/brianp/bin/raw2freq.bin.c -lgd -o /home/brianp/bin/raw2freq.bin_a  > ~/bin/gcc.log 2>&1


Still seeing weirdness in windows on \\192.168.10.103\brianp\brianp\bin\gcc.log:
/home/brianp/bin/bpbfct.c: In function â€˜radixSortâ€™:

The vi and gvim output are still correct in Ubuntu

Putty config window ->translation is se6t to "received data assumed to b in char set ISO-8859-1:1998(latin-1)
That looks right...

Has use Unicode line drawing code points...

Tried `set encoding=latin-1` and reran gcc. No difference...  Very puzzling

============================
Editor keeps clearing my posts???

---

### Post by steeldriver on 2016-01-25
Sorry I didn't mean to run that as a command in the Ubuntu shell, I meant to run it inside vim (or gvim) when you are viewing the file on the Windows box i.e. 

```

ESC 
:set encoding=utf-8

```

---

### Post by brian117 on 2016-01-25
It worked in gvim:
:
set encoding=utf-8
<enter>

Poof! The weird chars are all gone!
After recompiling, they are still gone...


Kill gvim, re-edit... There Ba-a-a-a-ak!

The set directive has a session scope. Every time I deal with Ubuntu, I will need to re-de-translate. 

This is certainly an improvement. Better than writing a seek and destroy Perl daemon...

But, how is this "feature" permanently disabled in Ubuntu?

---

### Post by steeldriver on 2016-01-25
You could add the 'set' command to your Windows vimrc file

---

### Post by brian117 on 2016-01-25
It worked in gvim:
:
set encoding=utf-8
<enter>

Poof! The weird chars are all gone!
After recompiling, they are still gone...


Kill gvim, re-edit... There Ba-a-a-a-ak!

The set directive has a session scope. Every time I deal with Ubuntu, I will need to re-de-translate. 

This is certainly an improvement. Better than writing a seek and destroy Perl daemon...

But, how is this "feature" permanently disabled in Ubuntu?

---

### Post by brian117 on 2016-01-25
>>  You could add the 'set' command to your Windows vimrc file

The root of the problem is that somebody has set an INTERNATIONALIZE flag to ON where it is not needed. All my data are being "upgraded" for me. 

This is going to bite me, I just know it!  I am going to write some file, the data will be scrambled and I will spend all day tracking down in my code where it got off in the weeds only to remember that Ubuntu didn't like Latin-1 and helped me out. 

I would rather not mask this symptom only to have it pop up elsewhere. 

For program development, I would not want anybody, however well-intentioned, monkeying with my code, reports or data. 

Suse does not alter your data. This is too heavy handed...

This is worse than microsoft adding LFs to CRs. Much harder to filter.

---

### Post by steeldriver on 2016-01-25
From the `buntu side, it would be a matter of setting a Windows-friendly locale, I think - for example, you could try

```

LC_CTYPE=ISO-8859-1 gcc -Wformat=0 *yadda yadda*  > ~/bin/gcc.log 2>&1

```

However I'm not sure what would happen if you were to set that globally (e.g. exported via your ~/.bashrc) - it might mess with the appearance of native applications

---

