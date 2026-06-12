---
title: "Named pipe versus standard text file?"
date: 2019-11-24
forum: General Help
---

### Post by croyle on 2019-11-24
Hi everyone,
I am working on a simple system maintenance script for updating repositories, upgrading packages, clearing cache, checking for broken packages, checking for orphaned process and packages just some simple house keeping tasks.  Well I am using dialog to display the progress to the user and make a log file and came across the 'mkfifo' command is there any advantage to using the mkfifo over just using a simple text file.  The man page for mkfifo is pretty sparse the only real difference I can see deals with setting SELinux security context to default or setting CTX , SMACK.  I found some information on google but it appears like mkfifo is legacy command.  Any information would be appreciated.

Thank you,
Jason

---

### Post by croyle on 2019-11-24
I think I figured this out in case anyone else is interested mkfifo makes it a lot easier to deal with the pipe file permission still not sure what SELinux, CTX or SMACK is but if I make a regular file with touch I have permission issues accessing it later in the script with redirecting command output.  When I create the pipe with mkfifo those permission issues dont seem to be a problem

[[ -f filename ]] || mkfifo filename 

then as end of script 
cat filename >> log
rm filename

I just like to do things the proper way as with most things in linux it appears with are multiple ways accomplish as task but weather by convention or security reason or just plan simpler there seems to be an accepted correct way to do it.

---

### Post by HermanAB on 2019-11-24
Well, a FIFO is a memory buffer that can be used to tie two processes together.  It is frequently used when working with slow serial ports, but it has other uses too.

---

