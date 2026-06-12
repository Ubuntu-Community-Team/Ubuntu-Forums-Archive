---
title: "plz help"
date: 2007-03-31
forum: General Help
---

### Post by virtual888 on 2007-03-31
i installed wubi and when the computer started i choose ubuntu , it write few line ,after this it write boot and plz wait.... , the computer did'nt think and i wait a long time and it did'nt move forward plz help me i want to try it 
thank you for your help
forgive me for my bad english :)

---

### Post by ago on 2007-03-31
Do you see the blue screen? What are the latest messages you can reed? Do you see logs in C:\wubi\logs? What HD / filesystem are you using?

---

### Post by virtual888 on 2007-03-31
ok i dont see the logs in C:\wubi\logs ,my HD IS western degital sata 80gb
i dont see a blue screen
the last messages are :
> 
boot
loading,please wait...
check root=booting cat /proc/cmdline or missing module ,devices cat /prod/modules 
alert! doent exit dropping to a shell
busybox.......
/bin/sh :cant access tty job control truned off 
(initramfas)_


thank you for your help...

---

### Post by ago on 2007-03-31
can you zip the logs folder and attach it here?

---

### Post by virtual888 on 2007-03-31
i dont see the logs in C:\wubi\logs ; there is not such a folder

---

### Post by ago on 2007-03-31
then when you get the prompt type: 

more  /logs/*

see if there is any relevant message

---

### Post by virtual888 on 2007-03-31
ok i typed and i get this msg :
> 
more: /logs/* NO SUCH file or directory


---

### Post by ago on 2007-03-31
no ":"
do also 
more /tmp/*

---

### Post by virtual888 on 2007-03-31
i didnt typed ":" i typed more /tmp/* 
and i get the msg : 
No such file or directory

---

### Post by hnfmr on 2007-03-31
I'm getting the same error too. Everything stops at "Loading, Please wait..."

---

### Post by virtual888 on 2007-03-31
i get this message too , after this i wait a long time like a 10 min and after this it wrote :

> check root=booting cat /proc/cmdline or missing module ,devices cat /prod/modules
alert! doent exit dropping to a shell
busybox.......
/bin/sh :cant access tty job control truned off
(initramfas)_

---

### Post by mpgarate on 2007-03-31
Ive been having this problem as well. I am trying the beta 2 right now, and If I still get the error ill try and post the results.

edit: same results, could not find the logs.

---

### Post by ago on 2007-03-31
Can you please report EXACTLY what you see between "looading..." and "busybox"?
See also if there is anything under /tmp. You may also want to try the latest minefield6 [http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield6.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-beta-minefield6.exe)

---

### Post by mwilley on 2007-03-31
Just wanted to add that I have this same problem with beta 2
After the "loading please wait..." it just sat there for about 5-10 minutes until the following code appeared... nothing special.

> check root=booting cat/proc/cmdline
or missing modules, devices: cat/proc/modules  1s/dev
ALERT! does not exist.  Dropping to shell

Will try the minefield now... I'll tell you if it works.

EDIT: Tried minefield 6... same response.

---

### Post by virtual888 on 2007-04-01
between "looading..." and "busybox" i see :

> 
check root=booting cat /proc/cmdline or missing module ,devices cat /prod/modules
alert! doent exit dropping to a shell

ok and also i typed  /tmp and the i get:
permission denied

i installed the latest minefield6  and it the same messages 

can someone help plz i want this very much ,thanks

---

### Post by ksglp on 2007-08-05
Hi, this is my current problem, did it ever get fixed? 
or can i just not use ubuntu?

---

### Post by ksglp on 2007-08-05
just so you don't have to look for the problem in the thread, after the ubuntu start screen comes up, and it doesn't load, after a few minutes i get this message

boot
loading,please wait...
check root=booting cat /proc/cmdline or missing module ,devices cat /prod/modules 
alert! doent exit dropping to a shell
busybox.......
/bin/sh :cant access tty job control truned off 
(initramfas)_ 

anyone got any ideas,

i've just reformatted my hard drive today in an attempt to solve the problem, with no luck, cheers for all the help you give,

Jordan

---

### Post by tuxcantfly on 2007-08-05
> i've just reformatted my hard drive today in an attempt to solve the problem, with no luck, cheers for all the help you give,

Well if you've already reformatted your hard drive, you might as well do a standard install of Ubuntu, or if you don't want to use a CD, try the netboot-install program I wrote, guide at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by ksglp on 2007-08-05
yeah, i am installing ubuntu using the cd, i'm just posting here because this is what came up when i searched for it, i can't install from the net because my computer now has no working OS,

any other ideas?

---

