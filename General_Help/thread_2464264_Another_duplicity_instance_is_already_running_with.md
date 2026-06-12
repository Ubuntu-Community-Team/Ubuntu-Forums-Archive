---
title: "Another duplicity instance is already running with this archive directory"
date: 2021-06-28
forum: General Help
---

### Post by dbee on 2021-06-28
I get this error when i try to backup ubuntu /home folder to Google drive...

> Another duplicity instance is already running with this archive directory

```

dara@laptop-20-04:~$ duplicity --version
duplicity 0.8.12

```

---

### Post by dbee on 2021-06-28
Another duplicity question for the experts out there.

Duplicity backups are stored as .tar.gz files. I know how to restore a duplicity backup. But how do I access files from the backup without doing a full restore?

---

### Post by dbee on 2021-06-28
I'm thinking i can either send a SIG KILL to a runaway Duplicity process or else delete a Duplicity lock file.

Where is the duplicity lock file kept btw?

---

### Post by dbee on 2021-06-29
So I've had a look at the duplicity docs and I've tried this...
> ara@laptop-20-04:~/git_repos/olf_git$ duplicity cleanup [https://drive.google.com/drive/folders/1RGLnGed3djjH-Ev8TtFZVLwi4i4C](https://drive.google.com/drive/folders/1RGLnGed3djjH-Ev8TtFZVLwi4i4C)
Password for 'None@drive.google.com': 
Attempt 1 failed. BackendException: Bad status code 405 reason Method Not Allowed.
Attempt 2 failed. BackendException: Bad status code 405 reason Method Not Allowed.

for my Google drive folder. My Google pass doesn't work though. I get a 405.

---

