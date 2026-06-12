---
title: "Need help on how to search"
date: 2022-02-14
forum: General Help
---

### Post by mugwump40 on 2022-02-14
I need to find out how to search for a file on Linux.  I'm using Ubuntu Mate 20.2.   I need to find a file named "wsjtx_log.adi" .  It is part of the WSJTX program and the program won't let me open the file as I should be able to.  It gives a message "Error scanning ADIF log  Invalid ADIF header".  I need to search for the log without using the program.

---

### Post by Bashing-om on 2022-02-14
mugwump40; Hello -

> 
 I need to find a file named "wsjtx_log.adi" .

 That is the job of "find" :D
run in terminal:
```

sudo find / -name wsjtx_log.adi

```

[INDENT]my bit to try and help
[/INDENT]

---

### Post by mugwump40 on 2022-02-15
> **Bashing-om said:**
> mugwump40; Hello -


 That is the job of "find" :D
run in terminal:
```

sudo find / -name wsjtx_log.adi

```

[INDENT]my bit to try and help
[/INDENT]

Thanks for your help!  I used find and the response is:       find: ‘/run/user/1000/gvfs’: Permission denied
                                                                                             /home/ron/.local/share/WSJT-X/wsjtx_log.adi
 
Tried a bunch of things and no good.  Any more suggestions?  I have a fear no log was ever created.

---

### Post by oldfred on 2022-02-15
Is this not the file you are looking for?

/home/ron/.local/share/WSJT-X/wsjtx_log.adi

---

### Post by mugwump40 on 2022-02-15
Yes, that is the file.  But it gives me the permission denied message.  When I CD into /ron and do ls, there is no ".local"  I'm not a newbie, but still a dumbie.  Been using Ubuntu for years.  BTW, I'm 81.

---

### Post by #&amp;thj^% on 2022-02-15
> **mugwump40 said:**
>   When I CD into /ron and do ls, there is no ".local"  I'm not a newbie, but still a dumbie.  Been using Ubuntu for years.  BTW, I'm 81.

Try using the -a flag>> ls -a
```
cd /home/me && ls -a

```
mine:
```
.                                           .ICEauthority
 ..                                          .icons
 ALT-80                                      .kde4
 .aqemu                                      .kodi
 .bash_aliases                               kolf.pdf
 .bash_history                               .lesshst
 .bash_logout                                **_[COLOR="#FF0000"].local[/COLOR]_**
 .bash_profile                               .mozilla
 .bashrc                                     Music
 .cache                                      .nanorc
 .cargo                                      .nordnm
 .cert                                       .nv
 .config                                     .nvidia-settings-rc
 .conky                                      Pictures
 conky-manager2                              .pki
 Desktop                                     Public
 .dmrc                                       .qomui
 Documents                                  'sudo nvidia-smi -pm 1 persisent mode and others'
 Downloads                                   Templates
 eos-log-tool.logs                           Videos
 eos-log-tool.logs.bak                       .wget-hsts
 ExtremeCooling4Linux-v0.3-x86_64.AppImage   .Xauthority
 .fonts                                      .xinitrc
 .gnupg                                      .xsession-errors
 .gtkrc-2.0                                  .xsession-errors.old

```
or:
```
cd /home/me/.local && ls -a
.  ..  share  state

```

---

### Post by mugwump40 on 2022-02-15
Thanks!  (I think.)  (-:  I finally got there but the results were not what I wanted.
~/.local/share/WSJT-X$ gopen wstjx_log.adi
The file /home/ron/.local/share/WSJT-X/wstjx_log.adi does not exist.
Guess it's time to do a complete new install.

---

### Post by mugwump40 on 2022-02-15
FINALLY!!  I was able find the file, copy and save to a new file.  Don't know why wsjtx won't open it, but at least I can fix it now!  Thanks to all and this problem is closed.

---

### Post by Bashing-om on 2022-02-15
mugwump40; Great :D

Good that you do have resolution.
As such >>
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]weren't nothing but a thing
[/INDENT]

---

