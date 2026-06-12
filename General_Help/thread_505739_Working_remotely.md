---
title: "Working remotely"
date: 2007-07-20
forum: General Help
---

### Post by boom2k1 on 2007-07-20
Is there a tool that integrates sftp-ssh file upload tool into a well known text editor?

What I want is a tool that would allow me to edit files from my harddrive that can easily be uploaded to the central school server via sftp-ssh.

The reason why I don't like using ssh -X is because sometimes the central sever is so jammed that I can't even run gedit or vi there.

Thanks in advance for replying.

---

### Post by bernied on 2007-07-20
You can mount a remote directory with sshfs.
You're supposed to be able to simply put a line into your /etc/fstab file, but I haven't managed to make this work. But from the command line it works fine.

Not sure if it's installed by default, if not it's just an apt-get (or whatever you use) away.

---

