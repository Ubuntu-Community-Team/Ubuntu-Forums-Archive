---
title: "export display"
date: 2008-05-16
forum: General Help
---

### Post by Hammer89 on 2008-05-16
I have two computer... one laptop and one desktop... and I'm trying to export the display of my desktop to my laptop. I ran "echo $DISPLAY" in terminal and it returned ":1.0." So then I logged into my desktop computer via SSH, and typed "export DISPLAY=<ip-address>:1.0"... however it isn't working. I have successfully exported my display previously using this method (on windows vista... which I had running an X server). So I'm not sure why this isn't working on Ubuntu... anyone know what I'm doing wrong?

---

### Post by bodhi.zazen on 2008-05-16
If you are forwarding X on your client use 

ssh -X

no need to set the display.

If you are trying to ssh into the server and run an X application on the server, that is more complex.

---

### Post by kthxbai2u on 2008-05-25
I am using Ubuntu 8.10 LTS or whatever... 

I have 8 servers, 2 of them I am currently working on. All using the same version. 

On *kthx* (desktop) I type **ssh -X root@DBServ** and enter the password. I then type **kate & ** and kate loads up running on *DBServ* but displaying on *kthx*. This works fine. This is what I expect to happen.

I do the same, but trying to connect to *WebServ* like so: **ssh -X root@WebServ** and enter my password.
 
I type **kate &** and get ```
root@WebServ:~# kate &
[1] 5384
root@WebServ:~# kate: cannot connect to X server

```

I have made sure *X11Forwarding = yes* in ssh_config and sshd_config on the server as well as did an **xhost +** on the client (kthx)

I have also looked through the gdm.conf and saw nothing wrong.

One thing I did notice is on *WebServ*, **echo $DISPLAY** always returns blank. On *DBServ* it returns "localhost:10.0". I don't think it should matter though because I'm hearing the -X makes the changing of $DISPLAY unnecessary.

All I want to do is load Quanta to do some PHP work on the site again :(

Thanks for the help! Sorry if i brought a dead post to life :-/

---

### Post by &amp;wP*!) on 2008-05-25
Just give **xhost +<machine name>** or even **xhost +<ip address>**. Or just give **xhost +**. Then try ssh, telnet or whatever. Let us know then, if it helps.

---

### Post by kthxbai2u on 2008-05-25
> **kthxbai2u said:**
> ... as well as did an **xhost +** on the client (kthx)...

you missed that... I did the **xhost +** already... same result.

---

### Post by &amp;wP*!) on 2008-05-25
> **kthxbai2u said:**
> you missed that... I did the **xhost +** already... same result.

Sorry, can you ping that machine? I know these questions are stupid but sometimes it helps.

---

### Post by kthxbai2u on 2008-05-25
of course i can ping it lol... I can connect to it via SSH why wouldn't i be able to ping it? lol... :) keep firing the ideas this way cause im all out of em :S

---

### Post by Prospero2006 on 2008-05-25
Try this: (Although I feel you are very close)

```

xhost +

ssh -X ip_addy_of_remote_machine

kate


```

That series of commands should work.

---

### Post by kthxbai2u on 2008-05-25
> **Prospero2006 said:**
> Try this: (Although I feel you are very close)

```

xhost +

ssh -X ip_addy_of_remote_machine

kate


```

That series of commands should work.

That series of commands is what I tried to do initially, and was asked by **pencuse** to do the same thing, and so as i told him, i will tell you: I did that already. Same results.

But, I seemed to have made things go downhill from there, now I cant get GDM/X to start. Soo... I will reinstall ubuntu (ouch)

Its a lot of work, but ill do it anyways... It would be too complicated to get someone to fix that problem when this one cant even be fixed O_o I know it needs to be given more time, but time is something I do not have :S

maybe somehow i screwed it up and (another) fresh install will work...

Ill keep you posted :)

---

