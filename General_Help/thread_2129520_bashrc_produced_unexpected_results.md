---
title: "bashrc produced unexpected results"
date: 2013-03-26
forum: General Help
---

### Post by zaphod_es on 2013-03-26
Creating an alias for my ssh command to my proxy server I added the line like this line to ~/.bashrc

alias linkname=`ssh -D 7777 -p 2299 [email]username@example.com[/email]`

Then to test it I fired up a new shell and, to my suprise, after a second or two of delay, it showed a login screen for my server at example.com.  Confused I remarked out the new line and started another new shell.  This did the expected thing and showed a local login screen.  Examination of my new line in .bashrc showed that I had used backticks instead of single quotes.  I changed the entry to 
alias linkname='ssh -D 7777 -p 2299 [email]username@example.com[/email]'
This now works as I intended and logs me into the remote server.

Can someone explain what happened and why? Are backticks part of the syntax for an alias?  Are there any interesting tricks I can use with them?

---

### Post by schragge on 2013-03-26
Backticks are used for command substitution in shell. The newer form of the same is $(...)
See
[http://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html](http://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html)
[http://tldp.org/LDP/abs/html/commandsub.html](http://tldp.org/LDP/abs/html/commandsub.html)
[http://wiki.bash-hackers.org/syntax/expansion/cmdsubst](http://wiki.bash-hackers.org/syntax/expansion/cmdsubst)

---

### Post by zaphod_es on 2013-03-26
Thanks, I sort of knew about command substitution but had not realised that, in effect, .bashrc is a script and runs commands.

---

