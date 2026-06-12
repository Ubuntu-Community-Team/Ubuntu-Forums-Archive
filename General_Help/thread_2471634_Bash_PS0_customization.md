---
title: "Bash PS0 customization"
date: 2022-02-05
forum: General Help
---

### Post by KBar on 2022-02-05
*The following is just my little story. The question is at the very bottom.*

[HR][/HR]My **PS1** contains a single backslash-escaped special character which prints out the current working directory:
```
~ echo "$PS1"
\w 
~ cd /etc/default/
/etc/default 
```

Now, what I also wanted is a timestamp of an entered command. **PS0** seemed like a perfect fit, so I set its value to the following:
```
/etc/default PS0='\t\n'
/etc/default cd /
11:25:01
/ ls
11:25:20
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  swapfile  usr
```
Well, that's awkward. I guess it's working as intended but this isn't exactly what I hoped for. I'd like the timestamp to appear besides **PS1** and not in a separate line.

Okay, it looks like it's time to have a long read through **console_codes**(4) and **terminfo**(5). 

I discovered a bunch of CSI sequences that control the cursor placement. F CPL especially seems like a good candidate. Surely this is it! Let's try it:
```
~ PS0='\033[1F\t\n'
11:33:22est
test
```
Ah, it scrambled all of the input. Perhaps I could use another sequence to prevent that:
```
~ PS0='\033[1F\033[9@\t\n'
11:35:29 ~ echo test
test
~
```
A-ha! That's what I call satisfying. I really love how my prompts look now. Just let me savor them a tad bit more:
```
~ echo "A-ha! That's what I call satisfying. I really love how my prompts look n
11:42:25 ow. Just let me savor them a tad bit more:"
A-ha! That's what I call satisfying. I really love how my prompts look now. Just
 let me savor them a tad bit more:
~
```
Well, that was unexpected. It looks like the definition of cursor movement sequences is too literal:
 > **console_codes(4)][FONT=courier new]A   CUU       Move cursor up the indicated # of rows.
       B   CUD       Move cursor down the indicated # of rows.
       C   CUF       Move cursor right the indicated # of columns.
       D   CUB       Move cursor left the indicated # of columns.
       E   CNL       Move cursor down the indicated # of rows, to column 1.
       F   CPL       Move cursor up the indicated # of rows, to column 1.
       G   CHA       Move cursor to indicated column in current row.
       H   CUP       Move cursor to the indicated row, column (origin at 1,1).[/FONT][/QUOTE]
So we're dealing with literal rows, which explains why **PS0** is only moved up a single row on the screen. Maybe escape sequences aren't what I need. How about something nice, elegant and extremely simple&#8212 said:**
> ```

          cursor_to_ll                ll        ll     last line, first
                                                       column (if no cup)
          cursor_up                   cuu1      up     up one line
```

That one looks much more promising! It deals in lines (hopefully, in **readline**'s definition of lines), not in rows. Let's see:
```
~ PS0="\$(tput cuu1)\033[9@\t\n"
~ echo "That one looks much more promising! It deals in lines (hopefully, in rea
12:02:25 dline's definition of lines), not in rows. Let's see:"
That one looks much more promising! It deals in lines (hopefully, in readline's 
definition of lines), not in rows. Let's see:
~ 
```
Nope! It lied. It also moves in literal rows. I went to bed furious and disappointed yesterday&#8230;[HR][/HR]I have **PS0** and **PS1** set to:
```
PS0='\033[1F\033[9@\t\n'
PS1='\w '
```
which works fine for simple commands:
```
12:09:38 ~ ls /
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  swapfile  usr
~
```
however, as soon as multiple arguments, pipelines or the sort get involved, the line is scrambled:
```
/ echo bin boot cdrom dev etc home lib lib32 lib64 libx32 lost+found media mnt o
12:13:48 pt proc root run sbin snap srv swapfile sys tmp usr var
bin boot cdrom dev etc home lib lib32 lib64 libx32 lost+found media mnt opt proc 
root run sbin snap srv swapfile sys tmp usr var
/
```
I've tried to manipulate the cursor via both **ECMA-48 CSI sequences** and **tput** caps. Unfortunately, both deal in literal rows, not **readline** lines. I have also tried saving the cursor location and restoring it:
```
PS0='\033[u\033[9@\t\n'
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[s\033[01;34m\]\w\[\033[00m\] '
~ 
~ echo 'bin boot cdrom dev etc home lib lib32 lib64 libx32 lost+found media mnt 
opt proc root run sbin snap srv swapfile sys tmp usr var'
12:38:37 ~ echo 'bin boot cdrom dev etc home lib lib32 lib64 libx32 lost+found m
bin boot cdrom dev etc home lib lib32 lib64 libx32 lost+found media mnt opt proc
 root run sbin snap srv swapfile sys tmp usr var
~ 

```
this kind of works except the first row is duplicated and it leads to some nasty stuff in extreme cases:
```
~ echo 'gkjghjk ghjgjh jjjjjjjjjjjjjjjjhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh'&#9166;






12:41:08 
gkjghjk ghjgjh jjjjjjjjjjjjjjjjhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh
~
```
[SIZE=4]So the question is (finally!):[/SIZE]
how do I combine both **PS0** and **PS1**, so that they appear together in a single **readline** line, side-by-side no matter the circumstances such as command line length or number of arguments? Ideally, this is what I want:
```
~ ### this is PS1
~ [ _command_string_ | _pipeline_ ] # command entered but not executed yet
12:52:56 ~ [ _command_string_ | _pipeline_ ] # command read and executed or is currently being executed
```

---

### Post by KBar on 2022-02-08
I sent an [email]("https://lists.gnu.org/archive/html/help-bash/2022-02/msg00020.html") to the [EMAIL="help-bash@gnu.org"]help-bash@gnu.org[/EMAIL] mailing list and Koichi Murase came up with a quite elegant workaround:
[QUOTE=Koichi Murase]Maybe this is just another hack that has some corner cases, but how about this?

bind -x '"\xC0\a":printf "%(%T)T "'
bind '"\xC0\r":accept-line'
bind '"\r":"\xC0\a\xC0\r"'

\C-j, \C-o, or other keybindings that execute commands can also be
rewritten in the same idea.

\xC0 + (7bit char) is an invalid two-byte UTF-8 sequence so will never
appear in the input stream as far as you are using UTF-8. If you do
not use UTF-8, these sequences should be replaced by something that
the current encoding does not contain or you will never use.

--
Koichi[/QUOTE]

This was already great. Nonetheless, they proposed an improved version just some minutes ago. Make sure to check out and follow the thread if you're interested.

---

