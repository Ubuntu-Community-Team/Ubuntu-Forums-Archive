---
title: "writing a script for the ps command"
date: 2008-04-22
forum: General Help
---

### Post by RichyGibson25 on 2008-04-22
hey guys I am trying to find a script command that shows the processes on that system for THAT user. I know I can just do a ps aux. But I am trying to make a script out of it. so if ANYONE uses the script it shows the processes for THAT user. Do i need to include some arguments in the script. i know from a local stand point i could do a ps ax | grep pts/0 but if i need to make it so anyone can run it and not have to edit the script, what type of changes do i need to make??

Thank you for any feedback!

~Richy

---

### Post by mister_pink on 2008-04-22
I was under the impression that it only showed your own ones anyway?

But otherwise, something like "ps -Ao args,%cpu,user|grep $USER" works. Do "man ps" and scroll down lots to find other format things you can add to the list of columns to show.

---

