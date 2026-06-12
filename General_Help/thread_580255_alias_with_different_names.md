---
title: "alias with different names"
date: 2007-10-18
forum: General Help
---

### Post by xhie on 2007-10-18
For the longest time I have been using an alias to connect to my schools server instead of typing out the whole thing:

alias clab='ssh [email]login@server.XXX.XXX.edu[/email]'

But last month they changed it so that we have to ssh into the different machines instead of just connecting to the server and it send us to a machine on its own. The machines all have the same naming convention, that is machine##.

So what I need to do (if it is possible) is to create an alias that would let me specify a number and use that in the ssh command

alias c##='ssh [email]login@machine##.XXX.XXX.edu[/email]'

so for example I would want to type c16 to connect to machine 16. 

Is this possible? How would I go about doing this? If not with aliases then is there another way to do what I am trying to do?

---

### Post by bodhi.zazen on 2007-10-18
Multiple alises will work just fine, as long as you have a unique alias for each c##

I assume you know to put 'em in ~/.bashrc

---

### Post by xhie on 2007-10-20
I know I can make multiple aliases, what I was asking was if there was a way I could make one and have it somehow plug in the number I type on the terminal.

Multiple ones is not problem, its just that there are 99 machines and I didnt want to stick 198 lines (99 for ssh and 99 for sftp) in the .bashrc file.

---

### Post by bodhi.zazen on 2007-10-21
> **xhie said:**
> I know I can make multiple aliases, what I was asking was if there was a way I could make one and have it somehow plug in the number I type on the terminal.

Multiple ones is not problem, its just that there are 99 machines and I didnt want to stick 198 lines (99 for ssh and 99 for sftp) in the .bashrc file.

LOL, I see now, sorry 

Add this to .bashrc :

> 
# ssh1
# use ssh1 # (where # = machine to login)

function ssh1 {ssh [email]login@machine"${@}".XXX.xxx.edu[/email]}

use ssh1 #<_of_machine>

Here I used 23 to show how it works :

> $ ssh1 23
ssh: machine23.XXX.xxx.edu: Name or service not known

---

