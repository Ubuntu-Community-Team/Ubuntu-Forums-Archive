---
title: "Setting colors for CLI systemwide (ubuntu 12.04)? Not for LS! But for colordiff etc."
date: 2013-08-05
forum: General Help
---

### Post by uluru13 on 2013-08-05
Hello Everyone

My google-searches for a solution must have doubled google's traffic today but have not surfaced a solution.

In order to avoid confusing one ubuntu server for another i defined different background colors in putty. 
Now my green background looks really good, until i use [s]certain commands[/s] colordiff: the lacking contrast is a torture to the eye.

While writing this post, my mistake dawned on me. 

**I struggled with the fact that **
```
colordiff test1 test2
```
**returned output that contained blue font!** and i was looking for a global way to change that. **how silly.**

**ANSWER: NOT POSSIBLE**
You can't _globally_ change the output of a specific command! I had already changed the default color of normal text! All commands already use it - but the output of colordiff is NOT "normal text" and therefore can only be defined specifically per user! Just create .colordiffrc insider a user's directory to change the colors:

Quote:"
# Example colordiffrc file for light backgrounds
#
# Set banner=no to suppress authorship info at top of
# colordiff output
banner=no
# By default, when colordiff output is being redirected
# to a file, it detects this and does not colour-highlight
# To make the patch file *include* colours, change the option
# below to 'yes'
color_patches=no
# 
# available colours are: white, yellow, green, blue,
#                        cyan, red, magenta, black,
#                        darkwhite, darkyellow, darkgreen,
#                        darkblue, darkcyan, darkred,
#                        darkmagenta, darkblack
#
# Can also specify 'none', 'normal' or 'off' which are all
# aliases for the same thing, namely "don't colour highlight
# this, use the default output colour"
#
plain=normal
newtext=darkblue
oldtext=darkred
diffstuff=darkgreen
cvsstuff=darkwhite
"
Taken from James Socol's [https://github.com/jsocol/dotfiles/blob/master/.colordiffrc](https://github.com/jsocol/dotfiles/blob/master/.colordiffrc)

More resources for setting CLI colors:
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)              Love sees no color. CLI does.
[http://blog.twistedcode.org/2008/04/lscolors-explained.html](http://blog.twistedcode.org/2008/04/lscolors-explained.html)             
[http://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html](http://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html)    Neat bash aliases
[http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/](http://ubuntugenius.wordpress.com/2011/07/11/how-to-change-the-command-line-prompt-colour-in-the-ubuntulinux-terminal/) Change console style
[http://leocharre.com/articles/setting-ls_colors-colors-of-directory-listings-in-bash-terminal/](http://leocharre.com/articles/setting-ls_colors-colors-of-directory-listings-in-bash-terminal/)
[http://linux.die.net/man/1/colordiff](http://linux.die.net/man/1/colordiff)

---

