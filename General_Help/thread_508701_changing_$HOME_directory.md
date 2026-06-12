---
title: "changing $HOME directory"
date: 2007-07-24
forum: General Help
---

### Post by jtprince on 2007-07-24
At work our /home directories mount to a remote server.  Lately (for some unknown reason) the server has been incredibly slow at doing its job.  To get around this, I do most of my work on a locally mounted directory.  However, almost every application reads/writes to dot files '~/.*' that are located in the home directory.  So, running almost any application becomes incredibly slow since it has to read/write to the files mounted on this slow server.

I am trying to move my home directory to a locally mounted directory until the problem is solved.  Since all login shells are supposed to go through /etc/profile, I inserted this into the /etc/profile directory:

[INDENT]if [ `whoami`=='john' ]; then
    export HOME=/work/john
fi[/INDENT]

Then, I moved all my home dot files to /work/john.

It works in the sense that after I login I can type 'cd' it takes me to /work/john and echo $HOME gives me '/work/john'.

However, when I log in I still end up starting inside of /home/john.  More importantly, my X11 connection is rejected (maybe because there is no .ssh folder?).  Also, the files .bash_history and .Xauthority are still written to /home/john.    How can I **completely** change the location of my home directory?

Many thanks

---

### Post by variona on 2007-07-24
In Ubuntu I'd do this with the usermod frontend (probably system-administration-user), in a shell use: sudo usermod -d /path/to/new/home -m MYLOGIN (I never actually have done this - better read man usermod yourself before blaming me afterwards ;)
variona

---

### Post by Mr. C. on 2007-07-24
You mean "mount from a remote server".

Your /etc/passwd file dictates where your home directory lives.  You can add/modify your own /etc/passwd and /etc/shadow entries.

If your company is using NIS to serve password entries, you will need to make sure the passwd and shadow entries in /etc/nsswitch.conf specify "files" before "nis".

If you need more help, let us know, and show the output of:
```

egrep '^passwd|^shadow|^group' /etc/nsswitch.conf

```

MrC

---

