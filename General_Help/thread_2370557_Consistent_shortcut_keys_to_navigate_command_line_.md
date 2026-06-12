---
title: "Consistent shortcut keys to navigate command line in Linux"
date: 2017-09-04
forum: General Help
---

### Post by Salil_Surendran on 2017-09-04
Hello,
   I use one set of keys to navigate the command line of my local desktop but when I ssh into another machine those same set of shortcuts don't work. For eg. Alt + f/b takes me forward/back on the command line of my local shell but not a remote machine. Even worse even on my local machine when I access terminal via IntelliJ on my local desktop the same shortcut keys don't work. Is there any way to set the same set of shortcut keys to do the same actions for different terminals.

---

### Post by TheFu on 2017-09-05
Would be best to learn the normal keystrokes for your shell to accomplish the same things.  Those work the same everywhere with the same shell.  Bash has a very rich command line editor. Learn it.  [https://www.gnu.org/software/bash/manual/html_node/Command-Line-Editing.html](https://www.gnu.org/software/bash/manual/html_node/Command-Line-Editing.html) It is highly efficient.

Concentrate on the ~/.inputrc file. This controls readline -  used by bash.  I got tired of not being able to easily delete the word to the right of my cursor.  cntl-w deletes the word to the left.  alt-w would be intuitive for removing the word to the right.  
```
$ more ~/.inputrc 

"\ew": shell-kill-word      # alt-w => delete word right
"\e[1;5C": forward-word     # Ctrl+right  => forward word
"\e[1;5D": backward-word    # Ctrl+left   => backward word

```
Of course, all the other stuff still works ---- ctl-e, ctl-a, .... 
 
For any customizations to "take", need to clone your bash setup between the systems, obviously.  Different systems have different setups.  Many people use a git repo for this.  I generally push my .bashrc, .bash_aliases, .inputrc and ~/bin/ to all systems where I get an account.  A little script could do it easily and consistently.

You might find the tips in here: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) useful as well.

---

