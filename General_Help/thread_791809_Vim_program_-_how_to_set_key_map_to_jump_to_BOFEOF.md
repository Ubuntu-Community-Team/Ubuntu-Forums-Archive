---
title: "Vim program - how to set key map to jump to BOF/EOF?"
date: 2008-05-12
forum: General Help
---

### Post by abcuser on 2008-05-12
Hi,
in vim program I would like to set that combination of <CTRL>+<Home> keys jumps cursor to beggining of file and the same way I would like to set that <CTRL>+<End> jumps cursor to end of file.

According to documentation from: [http://www.linux.com/articles/54936](http://www.linux.com/articles/54936) and [http://vimdoc.sourceforge.net/htmldoc/intro.html#%3CNul%3E](http://vimdoc.sourceforge.net/htmldoc/intro.html#%3CNul%3E) I should use map command. I tried the following to jump to BOF:
```

:map <C-Home> gg

```

For EOF I tried:
```

:map <C-End> G<End>

```

But none of the above commands work. Any idea how to set this two key mappings?

My system: Ubuntu 8.04 Desktop
BTW, I had installed vim-full package.
Regards,
Abcuser

---

### Post by drs305 on 2008-05-12
Unless I don't understand the question - when I'm in Vim typing  'gg'  automatically goes to the BOF and   'G'  goes to the EOF as long as I'm in the command mode. (Hit ESC first if you aren't sure).  Or are you looking to be able to use those commands without exiting the insert mode?

I haven't modified Vim in any manner. This is the way it works out of the box for me.

---

### Post by bingoUV on 2008-05-12
The way you have mapped your keys, it will work in normal mode (unless your terminal screws up, hope not). I guess you want it to work in insert mode. So, change your existing mappings to only work in normal mode, and add new mapping to work in insert mode. nnoremap maps for normal mode, inoremap maps for insert mode.
```

nnoremap <C-Home> gg
nnoremap <C-End> G<End>
inoremap <C-Home> <Esc>ggi
inoremap <C-End> <Esc>G<End>i

```

Hope you see the logic. In insert mode, before 'gg' and 'G', you have to go in normal mode. So I prefixed your mappings with <Esc>(to go to normal mode), and suffixed with i (to return to insert mode). See whether it works.

---

### Post by abcuser on 2008-05-13
> **drs305 said:**
> when I'm in Vim typing  'gg'  automatically goes to the BOF and   'G'  goes to the EOF as long as I'm in the command mode.Hi, I know 'gg' and 'G' works on my computer too. But I would like to use <CTRL>+<Home> instead of gg and <CTRL>+<End> instead of G<End>

---

### Post by abcuser on 2008-05-13
> **bingoUV said:**
> ```

nnoremap <C-Home> gg
nnoremap <C-End> G<End>
inoremap <C-Home> <Esc>ggi
inoremap <C-End> <Esc>G<End>i

```Hi,
I have tried this out and it does not work in my case. <CTRL>+<Home> jumps at beginning of line, but I would like to jump to beginning of file. <CTRL>+<End> jumps to end of line, but I would like to jump to end of file.

But according to documentation [http://www.linux.com/articles/54936](http://www.linux.com/articles/54936) "map - maps keys in normal, visual, and operator-pending mode" so map command should also work, but it doesn't in my case.

I got to work something wrong. Any idea what is wrong?
Regards,
Abcuser

---

### Post by abcuser on 2008-05-13
Hi,
I also tried:
:imap <C-Home> <Esc>ggi
Regards,
Abcuser

---

### Post by abcuser on 2008-05-13
I tried
:imap <Home> <Esc>ggi
and it works. So there is something wrong with <C-Home> command? Is this command correct, I just can't find out the exact syntax for this key combination.
Regards,
Abcuser

---

### Post by bingoUV on 2008-05-13
It is your terminal messing with the signal sent to vim. Do this, type upto (including space)
```

:imap 

```
Then press ctrl-v. Now type ctrl-home. This should get the signal produced by ctrl-home. Now go on to type 
```

 <Esc>ggi

```

---

### Post by abcuser on 2008-05-13
bingoUV,
you are righ, the <C-Home> key mapping does not exist! Pressing ctrl-v and then pressing ctrl-home combination solves the problem. This control character is then transformed into vim syntax: <Esc>OH which is for <CTRL>+<Home> combination and <Esc>OF which is for <CTRL>+<End> combination.

Now I have recognized that I need this key mapping in insert and normal mode so the final code put in ~/.vimrc is:
```
nmap <Esc>OH <Esc>gg
imap <Esc>OH <Esc>ggi
nmap <Esc>OF <Esc>G<End>
imap <Esc>OF <Esc>G<End>a
```
Thanks a lot,
Regards,
Abcuser

---

### Post by abcuser on 2008-05-13
Hi,
I have tested this little bit in deep and new problem arised :(
Now <Home> and <CTRL>+<Home> works the same way.

How to set <Home> to beginning of line (default settings in vim) and <Ctrl>+<Home> to beginning of file?
Regards,
Abcuser

---

### Post by bingoUV on 2008-05-13
After pressing ctrl-v, do ctrl-home and home produce same output?

---

### Post by doubi on 2011-11-20
Apologies for dredging up an old thread, but I'm having the exact same experience as abcuser up to this point, and it would be good to resolve the issue if possible.

So in answer to your question BingoUV, yes, Ctrl-Home and just Home seem to produce the same signal after Ctrl-v in your instructions (^[OH appears in both cases). Does that mean there's nothing I can do? Can I change the way gnome-terminal handles signals from the keyboard somehow?

---

### Post by abcuser on 2011-11-22
I was investigating this shortcuts, but at the end I learned the Vim way and I am quite happy with it.

Jump to start of file:
```
gg
```

Jump to end of file:
```
G
```
Note: G is <Shift>+g.

---

### Post by doubi on 2011-11-22
I use the vim commands for those functions too; unfortunately I wanted to map <C-Home> / <C-End> to something else :-) Specifically, when I'm using tabs, for jumping to the start and the end of the tab stack, or whatever it's called.

It would be good to get a general answer for achieving these mappings in gnome-terminal. One of the selling points I use for *nix (as well as vim) when proselytizing to non-users is configurability, so I always dislike hitting a wall with it :-)

---

### Post by abcuser on 2011-11-23
Hi,
you can change the keyboard mapping in Vim by using one of the 'map' command. Command imap is for insert-mode, nmap is for normal mode, vmap for visual mode etc. So each mode can have different mappings.

General syntax: {command} {key bindings that triggers the action} {vim commands to be executed}

For you sample pressing <Ctrl>+<Home> to jump to the first character of first line and <Ctrl>+<End> to the last character on the last line, do the following (type in the commands):
```

:nmap <C-Home> gg
:imap <C-Home> <Esc>gg
:nmap <C-End> G$
:imap <C-End> <Esc>G$

```
Above commands are valid for the current session. If you like to keep this settings when ever you start new vim session you need to save this settings in ~/.vimrc file, but in this file omit first ":" character.

For deeper understanding of mappings I suggest to read the following article:
[http://vim.wikia.com/wiki/Mapping_keys_in_Vim_-_Tutorial_%28Part_1%29](http://vim.wikia.com/wiki/Mapping_keys_in_Vim_-_Tutorial_%28Part_1%29)

Hope this helps.

---

### Post by doubi on 2011-11-23
Hi abcuser,

Yes, I'd tried approaches like this as suggested on the previous page.

The problem though is that we eventually discovered that the key-presses for 'Ctrl-Home' and 'Home' by itself are both sending the same signals to vim (^[OH).

So based on what bingoUV said above, this is no longer a vim issue, it's a gnome-terminal issue.

To see what I mean, taking your example, try to do:
```

:nmap <Home> gg
:nmap <Ctrl-Home> G

```
You'll see that now pressing both 'Home' *and* 'Ctrl-Home' result in jumping to the end of the file, i.e. the mapping for gg has been overridden by the mapping for G.

I hoped there would be some XML or gconf file somewhere where we could tinker with gnome-terminal's interpretation of different signals from the keyboard. It's very strange that it doesn't differentiate between these two when most every other text editor I can think of does so!

---

### Post by abcuser on 2011-11-23
> **doubi said:**
> 
```

:nmap <Ctrl-Home> G

```

You need to use <C-Home> not <Ctrl-Home>. But according to following post [http://stackoverflow.com/questions/3503252/how-to-remap-ctrl-home-to-go-to-first-line-in-file](http://stackoverflow.com/questions/3503252/how-to-remap-ctrl-home-to-go-to-first-line-in-file) it looks Terminal has some issues (probably as designed).

Try using xterm instead. You can start it from terminal using command: xterm
and then execute command: vim

I have tried this option with xterm and it works fine.

---

### Post by doubi on 2011-11-23
> **abcuser said:**
> according to following post [http://stackoverflow.com/questions/3...t-line-in-file]("http://stackoverflow.com/questions/3503252/how-to-remap-ctrl-home-to-go-to-first-line-in-file") it looks Terminal has some issues (probably as designed).

Try using xterm instead. You can start it from terminal using command: xterm
and then execute command: vim

I have tried this option with xterm and it works fine. 	

Fair enough. I think I'll search out some dev list for gnome-terminal before considering switching. Will post back if I find out anything useful.

---

