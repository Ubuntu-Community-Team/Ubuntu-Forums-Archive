---
title: "How do i set up OpenSSH and then connect to the server trough another computer?"
date: 2015-10-15
forum: General Help
---

### Post by Ashell_Seasucker on 2015-10-15
Hi i am working on a virtual machine with Ubuntu 14.04 LTS and i am wondering if i could get some help. But since i am new to Ubuntu and Linux overall i dont know how to do it. I have been trying to read up on SSH and other Ubuntu features on the Ubuntu server guide [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html) 


So i am wondering about how i should go about putting up a OpenSSH server. Since i need to be able to connect to it and accsess a printer.

---

### Post by mastablasta on 2015-10-15
does this help? : [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

where do you get stuck?

---

### Post by Ashell_Seasucker on 2015-10-16
Thx for the reply, but i was also wondering if there is any steps you need to take before you set up openSSH, want to be sure that i have done this correctly.
The thing about steps i am talking about is, what is needed before setting up openSSH.

---

### Post by Skaperen on 2015-10-16
there are *so many* possibilities.  what have *you* done to set up openssh?

step 1: find your network administrator

step 2: buy your network administrator a beer

...

---

### Post by Ashell_Seasucker on 2015-10-16
I dont think you know what i ment, what i am wondering about is, after you have installed Ubuntu on the viritual machine is there something before setting up openssh that i should do?

---

### Post by Skaperen on 2015-10-18
the only thing i have ever needed to do is make sure networking works and that the addresses are known.  that, and being sure you don't have any iptable blocks of port 22.  it is unusual that ssh would not work in this case. use telnet to test the port if the network setup on the VM might be the issue.

are you trying to connect *from* or *to* the guest system? printing should not need ssh unless you are using that to make a tunnel (-w or -L/-R).

---

### Post by deadflowr on 2015-10-18
> [COLOR=#000000]So i am wondering about how i should go about putting up a OpenSSH server. Since i need to be able to connect to it and accsess a printer.[/COLOR]

Why not use [CUPS]("https://help.ubuntu.com/12.04/serverguide/cups.html") for that?

---

### Post by Ashell_Seasucker on 2015-10-20
Got it to work now.

But my reason for asking about what steps i should take before setting it up is because i think to much about things that can go wrong, and therefore i want to be sure that i am not doing anything wrong.

---

### Post by efflandt on 2015-10-20
About all I do in /etc/ssh/sshd_config is set **PasswordAuthentication no** and use keys only. Even for my Android phone I use my Linux openssh keys (which require pass phrase). That way someone can try all the username/password hacking they want to and never get in. I think everything else is pretty much defaults.

---

### Post by HermanAB on 2015-10-21
The maintainers of SSH (OpenBSD) always try their level best to ensure that SSH is secure by default.  So you should not have to do anything special.

---

