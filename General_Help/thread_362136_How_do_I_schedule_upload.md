---
title: "How do I schedule upload?"
date: 2007-02-15
forum: General Help
---

### Post by webbber on 2007-02-15
Hi,
I was wondering if anyone knows how I can schedule uploads. This is my situation: 

- I can only upload at night because it hogs the line
- I have a very large photo directory that I would like to upload via FTP to my personal website
- It will take a few nights to upload I think
- Ideally I would like to be able to schedule the upload so that it starts uploading at say midnight, and stops at 8am. The next night, it will continue uploading from where it left off.

Does anyone know how to do this?
I am running KDE on kubuntu feisty.

ta.

---

### Post by webbber on 2007-02-15
I was thinking, I could use Kcron or cron in general and use some sort of command line FTP program with the settings to autoskip anything that already exists.

well thats the principle... can anyone make this a reality?!

---

### Post by charl.ie on 2007-02-15
Found the command ftp, and this checks the file .netrc (in your home dir) to see if it can automatically connect to a server. Hopefully this helps.

---

### Post by webbber on 2007-02-15
well thats something........ but not massively helpful......
someone else ......
please help!

sort me out!

---

### Post by phork on 2007-02-15
If you have ssh (and thus scp) access on your host rsync is the best way to go.  You can schedule a nightly job that will keep both directories completely in sync.  It only makes updates on what has changed, and can even delete files (if you want, not default) to keep both directories perfectly in sync.

---

### Post by webbber on 2007-02-16
Ok that sounds like exactly what I want! I'm going to find out from my host. cheers!

---

