---
title: "Prevent shut down when unsaved documents are open (16.04)"
date: 2017-05-02
forum: General Help
---

### Post by philgeiger on 2017-05-02
When I have an unsaved gedit document open and shut down Ubuntu in the standard way (button in the upper right corner, then "Shut down ..."), it just shuts down without waiting and asking me if I want to save the document.

I would like to change this, i.e., if there is an unsaved document open, **I always want to be asked if I want to save it before the system actually shuts down**. Is this possible?

I'm running 16.04. (I Have the feeling that in some previous version it worked precisely the way I wanted it to, but I may be wrong.)

Thanks,
Philipp

---

### Post by TheFu on 2017-05-02
Welcome to the forums.

[https://unix.stackexchange.com/questions/34489/how-to-disable-shutdown-so-that-an-important-process-cannot-be-interrupted](https://unix.stackexchange.com/questions/34489/how-to-disable-shutdown-so-that-an-important-process-cannot-be-interrupted) is all I could find.  Don't think it is possible. Ubuntu is Linux. Linux is based on Unix.  Unix systems do what they are told. The user is king.  If the user asks for anything stupid, the system should still do it, because it might be brilliant at the time. 

You could replace the shutdown command with something that does all the checking you want. Don't know how a GUI tells the system to shutdown. Sorry.

---

