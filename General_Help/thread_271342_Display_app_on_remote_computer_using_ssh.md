---
title: "Display app on remote computer using ssh?"
date: 2006-10-04
forum: General Help
---

### Post by Mr..Yeti on 2006-10-04
How do I run an app from a local computer and have it display on the remote computers screen?
 I want to use ssh, is it possible? What do i have to do to start it?

---

### Post by Ramses de Norre on 2006-10-04
You mean an X app? ```
ssh -X -l username host
command
```

This does only work on machines with an X client installed.

---

### Post by Mr..Yeti on 2006-10-04
Yes an X app.
That runs the command on the local computer, the one I log in from. I want to run, and display, the X app on remote server.

---

### Post by Ramses de Norre on 2006-10-04
Well, you log in to the remote machine with ssh -X and then from that ssh session you run the command to launch the application. This should open the app on the X client of your local machine, while the app will be running on the remote machine.

---

### Post by Mr..Yeti on 2006-10-04
> **Ramses de Norre said:**
> Well, you log in to the remote machine with ssh -X and then from that ssh session you run the command to launch the application. This should open the app on the X client of your local machine, while the app will be running on the remote machine.

ahh. That explains another problem I had. Thank you.
But for this task i want to start the app from the local machine, while the app is running on the remote machine and displayed on the remote X client.

I hope that makes sense.

---

### Post by Ramses de Norre on 2006-10-04
So you want to run an app so that it's displayed on the remote machine?

I was thinking maybe you could log in with a regular ssh into the remote machine, then in that session use ssh -X to log into the local machine and from that session run an X app.

I don't think this will work but it might and I don't know anything else to try.

---

### Post by RAOF on 2006-10-04
You can try (from an ssh terminal)
```

DISPLAY=:0.0 *program_to_run*

```
That'll tell the program to open on the X display 0.0, which is (usually) the   name of the X display.

---

### Post by Ramses de Norre on 2006-10-05
But doesn't any host has is own 0:0 display, so you need to execute the command from the remote machine then?
He wants to execute the app locally and make it appear remotely..

---

### Post by Mr..Yeti on 2006-10-05
> **RAOF said:**
> 
DISPLAY=:0.0 *program_to_run*


Cheers guys that worked. Just like i wanted it to.

Cheers both of you. Especially you Ramses de Norre and you RAOF.

---

