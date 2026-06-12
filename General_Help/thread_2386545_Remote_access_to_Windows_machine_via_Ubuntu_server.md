---
title: "Remote access to Windows machine via Ubuntu server?"
date: 2018-03-07
forum: General Help
---

### Post by delfiler on 2018-03-07
i might be asking something insane/impossible here but, is it possible to have an application on one pc able to run on another pc through an ubuntu server? for a more simplification i will call the two computers A and B.

so what i am asking is that there is an applacation on computer A that has to be able to run computer B through an ubuntu server without taking control of computer A or have the application on the ubuntu server

edit: might have been a bit unclear but both pc's are windows and the server is ubuntu hope this helps

---

### Post by kc1di on 2018-03-07
basically what your asking is what docker, [appimage]("https://appimage.org"), flatpacks, [snap]("https://www.ubuntu.com/desktop/snappy") and others do.  Do some research on[ containers]("https://www.infoworld.com/article/3204171/linux/what-is-docker-linux-containers-explained.html") and cloud apps. So all you'll have to do is load these packages in your ubuntu server and both machines can utilized them.  good luck.

---

### Post by delfiler on 2018-03-07
> **kc1di said:**
> basically what your asking is what docker, [appimage]("https://appimage.org"), flatpacks, [snap]("https://www.ubuntu.com/desktop/snappy") and others do.  Do some research on[ containers]("https://www.infoworld.com/article/3204171/linux/what-is-docker-linux-containers-explained.html") and cloud apps. So all you'll have to do is load these packages in your ubuntu server and both machines can utilized them.  good luck.

so what i am getting from you is that i have to install it on the server or am i mistaking? if i am mistaking that is my bad

edit1: so a repeat of what i did for the first post but for if you read this kc1di both of the pc's are windows pcs and the server is ubuntu

edit2: so if i did misunderstand or we misunderstood each other what i want is that the application stays on computer A but i can run it on computer B with out installing it on there while the ubuntu server provides a 'tunnel' or something (fairly new to ubuntu) that let's the app be run on computer B while also able to save the files on computer B, the saving of the files on computer B is not necessary but more for convenience otherwise there is always the old fashioned way of using an USB-stick

---

### Post by kc1di on 2018-03-07
I may have miss understood what your trying to do.  But I think it's not possible to run a program from computer a on compter b.  You may beable to run the same program on both and store the resultant files on the server so both computers can access them and use /modify them.  you may be able to run the program on computer a fro computer b by using ssh. or vice versa. but again you'll have to do the research. good luck.

---

### Post by delfiler on 2018-03-07
> **kc1di said:**
> I may have miss understood what your trying to do.  But I think it's not possible to run a program from computer a on comupter b.  You may beable to run the same program on both and store the resultant files on the server so both computers can access them and use /modify them.  you may be able to run the program on computer a fro computer b by using ssh. or vice versa. but again you'll have to do the research. good luck.

it can happen and that last part you wroth > **kc1di said:**
> you may be able to run the program on computer a fro computer b by using ssh. or vice versa doesn't that invalidate your first point when you wrote > **kc1di said:**
>  But I think it's not possible to run a program from computer a on computer b  but i will look into it

---

### Post by SeijiSensei on 2018-03-07
I don't see how the Ubuntu server plays any role here.  There is software to let you run one Windows machine remotely on another:  [https://www.lifewire.com/free-remote-access-software-tools-2625161](https://www.lifewire.com/free-remote-access-software-tools-2625161)

You could run an instance of Virtualbox or KVM on the Ubuntu server and run a Windows instance there.  You can run those remotely as well.

In the Unix world, it's easy to run a program on one machine and have the results display on another use the [X-forwarding]("https://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-to-run-graphics-applications-remotely") feature of SSH.  I don't think Windows has equivalent functionality, but it's been so long since I've run Windows seriously that I may be wrong.

---

### Post by wyliecoyoteuk on 2018-03-07
You can use Xforwarding over SSH using winSCP, I wrote an article about it a few years back, will see if I can find it.
There are Xservers available for windows also.
Or you could just use vnc on one pc to use the other's application.
I have in the past used one Linux PC with 2 X sessions both running VNC sessions to 2 remote windows PCs for 2 separate simultaneous users. X supports multiple sessions with multiple displays, mice and keyboards on one PC :)
Not sure what the OP is trying to do exactly.
[http://christoph-burmeister.eu/?p=1937](http://christoph-burmeister.eu/?p=1937)

---

### Post by wyliecoyoteuk on 2018-03-07
You can use Xforwarding over SSH using winSCP, I wrote an article about it a few years back, will see if I can find it.
There are Xservers available for windows also.
Or you could just use vnc on one pc to use the other's application.
I have in the past used one Linux PC with 2 X sessions both running VNC sessions to 2 remote windows PCs for 2 separate simultaneous users. X supports multiple sessions with multiple displays, mice and keyboards on one PC :)
Not sure what the OP is trying to do exactly.
[http://christoph-burmeister.eu/?p=1937](http://christoph-burmeister.eu/?p=1937)

---

### Post by QIII on 2018-03-07
Hello!

Without taking control of machine A?  Short answer:  No.

Desktop versions of Windows are not truly multi-user.  If your license on Windows computer A is for a single user desktop, then only a single user may be logged in to computer A at a time, no matter where the communication leads.  No matter remote desktop software you use.  Effectively, Windows computer A will be "taken over" by that user.  Windows Server, on the other hand allows for multiple users -- if you pay for multiple seats.

There is no way around this under the Windows EULA given the way that desktop versions of Windows are designed and provisioned.

---

