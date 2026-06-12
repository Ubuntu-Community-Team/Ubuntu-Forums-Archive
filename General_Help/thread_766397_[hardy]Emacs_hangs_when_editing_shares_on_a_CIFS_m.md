---
title: "[hardy]Emacs hangs when editing shares on a CIFS mount"
date: 2008-04-25
forum: General Help
---

### Post by lckarssen on 2008-04-25
Yesterday I upgraded my Gutsy workstation to Hardy. Since then I have troubles 95% of the time when editing a file on a CIFS mount using emacs. Emacs just hangs as soon as I try to change something in the file (like hitting enter, backspace, inserting a character, etc.). Moving around the file (before editing) works without problem. 
When emacs hangs there is an increase in network traffic. iptraf told me it was for port 445 which, according to /etc/services is ```
microsoft-ds    445/tcp                # Microsoft Naked CIFS
```
The share is mounted with the following script:
```
#!/bin/bash
/usr/bin/sudo mount -t cifs -o credentials=/home/lckarssen/.smb/cred,\
workgroup=remotegroup,uid=lckarssen,gid=users,\
file_mode=0640,dir_mode=0750 \
//server.mydomain.com/lckarssen /home/lckarssen/HomeServer
```

What I've tried so far:
- several files (plain text, LaTeX, C source code), but that doesn't seem to matter.
- start emacs with -q switch to disable my .emacs file
- start emacs with the -nw switch so that I don't open a window
- open a file with gvim or gedit and edit it. Works without problems. 
- remount the cifs share
- copy a file from the share to the local disk and then edit it: No problem...

Just to be sure:
- This worked perfectly before the upgrade
- The server runs Red Hat Enterprise and has not changed (as far as I know).

---

