---
title: "General Questions"
date: 2006-12-29
forum: General Help
---

### Post by fredster001 on 2006-12-29
Hi everybody,

I successfully installed ubuntu yesterday and like it. I have a few questions that may sound simple but i want to be sure...

1. Can i run ubuntu and windows 2000 when i turn on my laptop, and then switch between them, or to use the other one do i have to resttart my machine?

2. I partitioned part of my C Drive for windows and part for ubuntu, when in one OS can i access the other part?

3. Does the macromedia MX suite work in ubuntu?

4. The instant messenger in ubuntu, how do i make that work with my MSN account?


(This one will probably make some of you sigh but im new to it remember...)

4. When i look round the forum i see people saying "type in this code" etc. Where do you type it in??

Thanks 

fredster001

---

### Post by meng on 2006-12-29
1. Best to restart, you can run one OS within another using a virtual machine but unless your laptop is the bees knees, I wouldn't do it.
2. Yes. Give more details if you have trouble.
3. Yes, but only under wine or Crossover Office running in Ubuntu.
4. The terminal/console/command line. All names for the same thing.

---

### Post by fredster001 on 2006-12-29
cheers, can u explain what you mean about the MX suite...

also, about accessing the other part of the drive, where do i go to do that?

thanks

---

### Post by meng on 2006-12-29
3. Macromedia MX is only produced for windows not linux. Wine or Crossover Office is a windows compatibility layer that runs in linux. Therefore if you need to use Macromedia, you would install wine (or Crossover Office, a commercial version) in Linux.

4a. You start gaim, add a new account, choose MSN, I think you need to add @hotmail.com to the end of the username. Then connect using this account.

---

### Post by stalker145 on 2006-12-29
> **fredster001 said:**
> 1. Can i run ubuntu and windows 2000 when i turn on my laptop, and then switch between them, or to use the other one do i have to resttart my machine?

2. I partitioned part of my C Drive for windows and part for ubuntu, when in one OS can i access the other part?

3. Does the macromedia MX suite work in ubuntu?

4. The instant messenger in ubuntu, how do i make that work with my MSN account?

5. When i look round the forum i see people saying "type in this code" etc. Where do you type it in??

Welcome to the family :D 

1. You can't do this the way that I'm sure you're thinking. You will, basically, have to install a program called VMWare, qemu, or some other virtualization program and then install the operating system into that program. There are tutorials for each choice around here somewhere.
2. I'm rather sure that you can do this, though I don't know how off-hand.
3. Dunno.
4. OK, one I can help with ;)  Open up GAIM and choose to add an account <ctrl+a> or Accounts->Add/Edit, choose Add, and choose your provider (MSN, in this case) from the Protocol drop-down.
5. The place that you are typing in the code is into the Terminal. You can either press <alt+F2> and type gnome-terminal or you can go to your applications menu and choose Terminal under Accessories.

Good questions, all. Keep them coming.

---

