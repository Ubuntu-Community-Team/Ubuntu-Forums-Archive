---
title: "Access linux shel from windows"
date: 2006-11-21
forum: General Help
---

### Post by phillips321 on 2006-11-21
Hi there guys,

I usually VNC into my Linux box but now and again the VNC server locks up meaning the box is switched on but i cant access it remotely to reboot it or restart the VNC service.

I understand that i can create a wrapper for the VNC program that checks if the VNC server is running and if not it starts it but if the VNC program stalls but doesn't close the wrapper wont know to restart it.

What i would like to do is to be able to access the command line of the Linux Box from a different computer(windows) so that i can issue a restart of the VNC server of just simply reboot the computer alltogether.

Many thanks in advance for the help i might get

Matthew Phillips

Note to Admin: If this is posted in the wrong directory please accept my appologies and move to correct location.

---

### Post by Preserved Killick on 2006-11-21
Take a look at a program called putty.

I used to use putty to get a shell through my Windows machine on my Libranet linux box.  Haven't tried it yet to connect to Ubuntu, but it should work.  

Putty gets you an ssh login.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

-- Preserved Killick

---

### Post by phillips321 on 2006-11-21
so is putty the server or the client?

sorry but i allways thought putty was the client used...im confused.

---

### Post by karamba_kid on 2006-11-22
Putty is an SSH client for windows.  Your Ubuntu install already has a great solution to remotely access the linux command line and it's called OpenSSH.  SSH stands for secure shell so (if implemented correctly) it supplies you with industrial grade security.  I added in the "implemented correctly" comment because you still need to be knowledgable about the integrity of the machine you are using to connect to the remote server and you also need to be sure not to fall into a Man-in-the-Middle (MITM) type of attack.  Luckily the server supplies a RSA and/or DSA fingerprint so you can verify that your communicating with the correct server.  Check out the documentation at [http://www.openssh.org](http://www.openssh.org)

---

### Post by phillips321 on 2006-11-22
ok all sorted now, i installed the ssh package which made me also install the openssh package.

On my windows box i downloaded the single putty.exe and im now using that, it works great, cheers guys.

---

