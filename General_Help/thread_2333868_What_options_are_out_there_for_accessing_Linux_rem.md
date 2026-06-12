---
title: "What options are out there for accessing Linux remotely from Windows?"
date: 2016-08-14
forum: General Help
---

### Post by arsinek on 2016-08-14
I've looked around a little on this subject and it seems there are many options. I guess I am looking for some help in narrowing down a path to take so I can remote into my Ubuntu box from my Windows box.

One person told me to get PuTTY and that was all they said. I think I've seen PuTTY uses SSH.
Will PuTTY allow me to remote into my Ubuntu machine the same way Windows remote desktop lets you remote into other Windows machines?
Or is PuTTY only command line?
How does PuTTY work and what can I do with it?

Then I saw an article that suggested Remmina.
Remmina seemed like it might be more like Windows built in remote desktop.
Does anyone have experience with Remmina?

Thanks!

---

### Post by coldraven on 2016-08-14
PuTTY is a terminal emulator and file transfer application it is not a remote desktop.
[https://en.wikipedia.org/wiki/PuTTY](https://en.wikipedia.org/wiki/PuTTY)

---

### Post by irvine_himself2 on 2016-08-14
Since, at the moment, I only have a single laptop, its not really an issue for me. But, a few years ago, I was running Ubuntu and needed to be able to quickly/frequently run  proprietary windows software from Ubuntu. As I recall, all I did was to set up a home network  using Samba with an old Xp laptop. Then, it was just a case of using the remote access features of both Os. I even had a little quick launch Icon on the Ubuntu desktop to switch into the windows box. The only real problem was Samba continually prompting for passwords.   

Good luck, 
 Irvine

---

### Post by sudodus on 2016-08-14
One alternative is to install **openssh-server** in Ubuntu. You will be able to log in via ***ssh*** or other programs that use the ssh protocol, and access/transfer files with FileZilla or WinSCP from Windows.

---

### Post by coldraven on 2016-08-14
Is this any help? I don't have any Windows machine to try it out.
[https://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](https://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)

---

### Post by QIII on 2016-08-14
You need a secure connection such as SSH if you are going to do this over the web.

In my opinion, the best technology for this sort of thing is NX -- and the best way to get it all in a neat package is NoMachine.  [https://www.nomachine.com/](https://www.nomachine.com/)

NoMachine NX is no longer open source, but it is free for personal use.  It has a Windows client so you can remote from Windows to Linux easily.

NX is far superior in performance than anything else and NoMachine NX uses a secure implementation of SSH by default.

---

### Post by arsinek on 2016-08-14
> **coldraven said:**
> PuTTY is a terminal emulator and file transfer application it is not a remote desktop.
[https://en.wikipedia.org/wiki/PuTTY](https://en.wikipedia.org/wiki/PuTTY)

A remote terminal yes?
As in I'm on my Windows machine executing command line commands on my Linux machine through PuTTY?



> **QIII said:**
> You need a secure connection such as SSH if you are going to do this over the web.

In my opinion, the best technology for this sort of thing is NX -- and the best way to get it all in a neat package is NoMachine.  [https://www.nomachine.com/](https://www.nomachine.com/)

NoMachine NX is no longer open source, but it is free for personal use.  It has a Windows client so you can remote from Windows to Linux easily.

NX is far superior in performance than anything else and NoMachine NX uses a secure implementation of SSH by default.

Thanks! That does sound like a good option. I think I might go the PuTTY route though just to force myself to use the command line.

---

