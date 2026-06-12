---
title: "grep / cat question"
date: 2008-03-20
forum: General Help
---

### Post by xsystemx on 2008-03-20
I have installed webmin and I am trying to modify a cron job and getting the following error message: 

Failed to save cron job : Missing or invalid start date in range to run Day '' out of range 1..31 at ./cron-lib.pl line 811

**How can I grep or cat that file to display me line 811 ? Also, what is the recommended text editor for making changes "nano" ?**

---

### Post by x1a4 on 2008-03-20
grep searches for a text pattern.  Use it like so: 
```
cat <filename> | grep -n <pattern>
```
where <pattern> is the text string to search for.  The -n option will display which line <pattern> is found in.  

The best way to solve your issue however is to open cron-lib.pl and scroll down to line 811 and correct the problem. 

Which text editor to use is entirely a personal choice.  Many people on these forums use nano because it's easy to use and installed on all Ubuntu variants by default.  Personally I use vim, although it takes a little getting used to.  Install the **vim-full** package if you want to use it.  

You can also use a graphical text editor.  Simply run ```
sudo -s
``` to get root priviledges, this way you won't have to run sudo with every command and be able to launch graphical applications.  As you work you execute a graphical text editor (gEdit, jEdit, gVim, etc.), edit your file, close the editor and continue to work on the command line.

---

### Post by xsystemx on 2008-03-20
Using nano/vim, do I need to count to 811 in order to find the correct line of text?

---

### Post by x1a4 on 2008-03-20
To display line numbers in vim: 

When you open a file press the colon (:) and type **set number**
To show line numbers by default, put **set number** in your ~/.vimrc file. 

To display line numbers in nano press Ctrl+C to get the current position of the cursor.

---

### Post by spec-chum on 2008-03-20
With vim just open up the file and enter

:811

That'll jump to line 811.

---

