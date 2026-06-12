---
title: "Linux Server that will store all user files"
date: 2013-09-19
forum: General Help
---

### Post by whitelinux on 2013-09-19
Hi,

Whilst my linux experience is growing I have never run in a local office client/server environment.

I would like to do the following:

1. Linux Server that will store all user files
2. 10 Client machines that will on boot up load their files from the server or run them live from the server
3. Users will be able to login from any machine to their files (a bit like windows roaming profiles) although this is non essential and if a pain I could leave it.

The reason I want to do this is have a central file location to make backup and viewing of files by administrators easier.

If someone could advise me on hardware specs and a general idea of how I would do it with software?

Thanks,
Jerry

---

### Post by Lars Noodén on 2013-09-19
You could probably do all three quite well with Samba4.  

There is some community documentation on setting up Samba:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

A bit has changed with Samba4, which gives it more capabilities.

It won't cause that much of a demand on your hardware, so you can run the test with whatever you have available.

---

### Post by mastablasta on 2013-09-19
have you checked Zentyal (Ubuntu based) or ClearOS (red hat based)?

if it's only file server perhaps also OpenMediaVault (debian based).

Ubuntu server can do all that but you might want something that is easy to configure (not that ubuntu is hard) with a nice GUI.

another GUI option is install ubutnu server and then install *webmin* to it. 

servers are then administered via web browser GUI

---

