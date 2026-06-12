---
title: "i remove /etc/vim/vimrc files but vi does not care"
date: 2022-01-21
forum: General Help
---

### Post by centguy2 on 2022-01-21
When a user runs vim, is the behavior controlled by /etc/vim/vimrc ?

It does not seem to read that file.

Where is  debian.vim mentioned in that file?

What is VIMRUNTIME?

---

### Post by centguy2 on 2022-01-21
My specific question is:
Where is the file that asks the cursor location to be remembered?

 The default vimrc has this turned off..

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif

So how to ask the vi to forget the last cursor position when I open a file under vi?

---

### Post by &amp;KyT$0P# on 2022-01-22
> **centguy2 said:**
> So how to ask the vi to forget the last cursor position when I open a file under vi?

Put this line in [FONT=Courier New]/etc/vim/vimrc.local[/FONT] -
```
augroup vimStartup | au! | augroup END
```

Then delete [FONT=Courier New]~/.viminfo[/FONT] before starting vim again.

---

### Post by schragge on 2022-01-22
> **centguy2 said:**
> What is VIMRUNTIME?
```
ex +'ec $VIMRUNTIME|q'
```
> **centguy2 said:**
> Where is  debian.vim mentioned in that file?
```
ls $(vim -eT dumb --cmd 'exe "se t_cm=\<C-M>"|ec $VIMRUNTIME|q'|tr -d \\r)/deb*
```

---

### Post by centguy2 on 2022-01-24
[ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar2034672_1.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=2034672") 				 				 					 						 	[**[COLOR=#000000]halogen2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2034672")  

root@ubuntu-inspiron:/etc/vim# cat vimrc.local
augroup vimStartup | au! | augroup END


It still remember the last location!

Debian vim is still more consistent for some reason...

---

### Post by schragge on 2022-01-24
By chance, do you have **vim-lastplace** installed?

---

### Post by &amp;KyT$0P# on 2022-01-24
> **centguy2 said:**
> halogen2

root@ubuntu-inspiron:/etc/vim# cat vimrc.local
augroup vimStartup | au! | augroup END


It still remember the last location!

Does your [FONT=Courier New]/etc/vim/vimrc[/FONT] have these lines that are in the default [FONT=Courier New]/etc/vim/vimrc[/FONT]? -
```
" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif
```

---

### Post by centguy2 on 2022-01-24
Does your [FONT=Courier New]/etc/vim/vimrc[/FONT] have these lines that are in the default [FONT=Courier New]/etc/vim/vimrc[/FONT]? -

Answer: Yes. I understand that is to ask the system to read /etc/vim/vimrc.local. 

So it still won't work.


BUT going by that logic, I put 

[FONT=Courier New][/FONT][FONT=Courier New][/FONT]augroup vimStartup | au! | augroup END

in ~/.vimrc

and it works.

But I won't call that a solution. Something is really wrong with the vim setup. Debian does not have this problem.
For me the vim situation in ubuntu  needs to be fixed to gain my confidence. Just my opinion.

---

### Post by &amp;KyT$0P# on 2022-01-26
I had to put the following at the very top of my [FONT=Courier New]/etc/vim/vimrc.local[/FONT] to get that file to override the default configuration, maybe it's needed here too? -
```
if filereadable($VIMRUNTIME . "/defaults.vim")
  source $VIMRUNTIME/defaults.vim
endif
let g:skip_defaults_vim=1
```

---

### Post by centguy2 on 2022-01-26
Make this line 
active
```

let g:skip_defaults_vim = 1

```

and all problems gone! The loading of the defaults make the behavior very random. I spent a few hours and almost went crazy.

Thanks for the hint. 

I am both relieved and angry at the same time.

---

