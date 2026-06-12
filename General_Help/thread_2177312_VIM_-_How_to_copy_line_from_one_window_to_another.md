---
title: "VIM - How to copy line from one window to another"
date: 2013-09-28
forum: General Help
---

### Post by CkDGTAT on 2013-09-28
Hi,

I need a command that would copy the line from one window and paste it to another window.

I tried to use

```
:.w >> file 

E139: file is loaded in another buffer
```
 
Thanks

---

### Post by Impavidus on 2013-09-28
From the [vimbook](ftp://ftp.vim.org/pub/vim/doc/book/vimbook-OPL.pdf) page 163:> 
In this method, you start up two Vim programs and copy text from one to another.
You do this by using the system Clipboard register ("*).
1. Edit the first file.
2. Start another Vim program to edit the second file.
3. Go to the window with the first file in it.
4. Go to the start of the text to be copied.
5. Issue the V command to start visual mode.
6. Go to the end of the text to be copied.The selected text will be highlighted.
7. Use the "*y command to yank (copy in Microsoft parlance) the text into the system Clipboard register ("*).
8. Change to the other editing command. (Make that editor your active window.)
9. Go to the line where the insert is to occur.The text will be placed before this line.
10. Issue the command "*P to put (paste in Microsoft terminology) the text in the system Clipboard register ("*) above the current line.

Note
This method enables you to not only move text between two Vim applications, but also to &#8220;yank&#8221; and &#8220;put&#8221; between Vim and other applications as well. For example, you can select text in an xterm window using the mouse and paste it into a Vim editing using "*P. Or you can copy text into the system register in a Vim session and paste it into a Microsoft Word document using the Edit, Paste commands.

---

