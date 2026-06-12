---
title: "Anacron job 'cron.daily' error messages"
date: 2008-06-20
forum: General Help
---

### Post by rutgerw on 2008-06-20
Every morning I get the following email indicating an cron error:

gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster 'at' ubuntu.com>" not
changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage 'at' ubuntu.com>" not
changed
gpg: Total number processed: 1
gpg:              unchanged: 1

I've tried removing the keys and adding them again using apt-key; no success

Just removing the keys; no success

I tried piping the STDOUT of the script to /dev/null with no success (pipe was added in the cron job)thus it must be an error. Strangely, when I call the script as root, it exits clean.

Googling for the problem led me to "Bug #192074 in apt (Ubuntu)" which should have been fixed on 2008-03-04

Has anyone got a clue how to get rid of these annoying emails?

---

### Post by rutgerw on 2008-08-07
I'm Still having these problems with /etc/cron.daily/apt.

Really no one here who knows an answer to this?

---

