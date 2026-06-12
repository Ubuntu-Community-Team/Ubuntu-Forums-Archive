---
title: "Compiled code not crashing and crashing!"
date: 2014-04-24
forum: General Help
---

### Post by h.hittini on 2014-04-24
Hello there,

I compiled the attached files using ```
gcc sctpserver.c -lsctp -o server && gcc sctpclient.c -lsctp -o client
``` and I didn't get any errors
The source files are found here [http://www.opensourceforu.com/2011/12/socket-api-part-5-sctp/#](http://www.opensourceforu.com/2011/12/socket-api-part-5-sctp/#)
I have two machines running Ubuntu Server 10.04 LTS and 2.6.32-55-generic kernel
Machine 1: [http://www.dell.com/us/dfb/p/optiplex-755/pd](http://www.dell.com/us/dfb/p/optiplex-755/pd)
Machine 2: [http://www.roboard.com/RB-110.htm](http://www.roboard.com/RB-110.htm)
I tried running the server and the client (attached) on Machine 1 and Machine 2 respectively and they worked, even the vice versa worked fine
After that, I downloaded a desktop environment on Machine 1 using ```
apt-get install ubuntu-desktop
```
After the install, when having the server on Machine 2 and the client on Machine 1 everything works fine
However, when having the server on Machine 1 and the client on Machine 2 the server crashes
Any ideas?

Thank you

---

### Post by Impavidus on 2014-04-24
Ubuntu 10.04 desktop version is unsupported, so by installing ubuntu-desktop something may have gone wrong. I can't say what exactly.

---

### Post by h.hittini on 2014-04-24
> **Impavidus said:**
> Ubuntu 10.04 desktop version is unsupported, so by installing ubuntu-desktop something may have gone wrong. I can't say what exactly.

The server version is supported until April, 2015 [http://en.wikipedia.org/wiki/Ubuntu_10.04_Lucid_Lynx#Ubuntu_10.04_LTS_.28Lucid_Lynx.29](http://en.wikipedia.org/wiki/Ubuntu_10.04_Lucid_Lynx#Ubuntu_10.04_LTS_.28Lucid_Lynx.29)

---

### Post by Impavidus on 2014-04-24
Yes, I know the server version is still supported, but I think the ubuntu-desktop package is part of the desktop version. They shared the same repositories, which are still active for the server version, but this package is no longer supported. I imagine it (or one of its many dependencies) could cause a conflict with the latest server packages.

---

### Post by h.hittini on 2014-04-24
> **Impavidus said:**
> Yes, I know the server version is still supported, but I think the ubuntu-desktop package is part of the desktop version. They shared the same repositories, which are still active for the server version, but this package is no longer supported. I imagine it (or one of its many dependencies) could cause a conflict with the latest server packages.

I compared the version I have of "ubuntu-desktop" and the version available here [http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop) and they are the same, so, I have the latest version
Do you have any suggestions? because I need a desktop environment on that server

---

### Post by Impavidus on 2014-04-24
Yes, the ubuntu-desktop package on lucid hasn't been updated for a year, so if you installed it recently you must have the latest version. The point is, as it is no longer supported the latest version may be outdated.

You could install a version of Ubuntu with the desktop version still supported. There may be other solutions, so you could wait a day and hope somebody else posts an idea.

---

### Post by h.hittini on 2014-04-26
> **Impavidus said:**
> Yes, the ubuntu-desktop package on lucid hasn't been updated for a year, so if you installed it recently you must have the latest version. The point is, as it is no longer supported the latest version may be outdated.

You could install a version of Ubuntu with the desktop version still supported. There may be other solutions, so you could wait a day and hope somebody else posts an idea.

The problem is Machine 2 doesn't support 3.X kernel; it has an old processor and Ubuntu 10.04 Server appears to be the only version running 2.6 kernel and still supported
And I need both machines to run the same kernel
Thanks anyway :):)

---

### Post by Impavidus on 2014-04-26
There are other linux distros that may still support a desktop version on a 2.6 kernel. I don't know any specifics.

---

### Post by spjackson on 2014-04-29
While it is possible that the desktop packages have a significant impact on the example code you are trying to run, you don't present a great deal of evidence for that. Your apt-get install may have done something major that affects your program, or it may have done something minor, or it may be a coincidence.

I suggest you debug your crashing program, and indeed turn it from example code to production quality code by adding tests on return values and errno when making low level system calls.

---

