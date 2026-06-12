---
title: "Vim Persmission Denied?"
date: 2008-04-13
forum: General Help
---

### Post by zJerrik on 2008-04-13
I'm new to Linux (Using Ubuntu Hardy Heron) and I'm learning Vim, but everytime I save a file and try to run it using:

./filename

It gives me "bash: ./filename: Permission denied". Does anyone have an idea why? Here is the general steps I take to make a new file in vim.


vim
:insert
[type some text]
[esc_key]
:save filename
:quit or :q

I think either I need to set something in the file when I'm editing using vim, or I'm using the wrong command to display the text in that file?

Thanks for the help, sorry if this is in the wrong category, I've only started lurking.

---

### Post by schnittchen on 2008-04-14
You are writing a script to be executed?
If so, you need to set the appropriate execute permission on the file.

You can find out the current permissions with

ls -l filename

You should get something like

-rw-r--r--  1 username username

In short, having no "x" in the first column means that the file is not executable.
If you want the file to be executable by yourself, and you created the file, do

chmod u+x filename

You can learn more about file permissions here:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

