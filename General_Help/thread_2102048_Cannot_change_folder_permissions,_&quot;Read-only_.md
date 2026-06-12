---
title: "Cannot change folder permissions, &quot;Read-only file system&quot;"
date: 2013-01-06
forum: General Help
---

### Post by c3ntury on 2013-01-06
OS Version: Maverick 10.10 x64.

Screenshot (includes hard-drive information and such) -
[IMG]http://i.imgur.com/prrMC.png[/IMG]

Whenever I try and change the permissions of a folder, it gives me this error. What can I do to fix this?

I tried Googling, and discovered that chmod wasn't working because it 'writes' data in some shape or form. 

In addition, I thought I might be able to remount it, **but I'm not sure how to do this safety, as I do not have physical access to the machine**, and only have terminal access (I have a VNC server set-up, but it's a pain to use for me).

What can I do?

Thanks and best regards,
Cameron.

---

### Post by dcstar on 2013-01-06
> **c3ntury said:**
> 
.........
What can I do?


The file system needs a **fsck** done on it, if you can unmount it remotely then it should be easy to fix.

---

### Post by catalin.vasilescu on 2013-01-07
unmount the partition
make fsck
mount it back

---

### Post by dcstar on 2013-01-07
> **catalin.vasilescu said:**
> 
make fsck


"**make**" is used to compile programs, it is totally out of context to tell people to use it in this situation and can only serve to mislead the OP.

If you do not understand the problem please do not offer things that are not appropriate.

---

### Post by catalin.vasilescu on 2013-01-07
> "**make**" is used to compile programs,
= run the command fsck

---

### Post by fdrake on 2013-01-07
> **c3ntury said:**
> OS Version: Maverick 10.10 x64.

Screenshot (includes hard-drive information and such) -
[IMG]http://i.imgur.com/prrMC.png[/IMG]

Whenever I try and change the permissions of a folder, it gives me this error. What can I do to fix this?

I tried Googling, and discovered that chmod wasn't working because it 'writes' data in some shape or form. 

In addition, I thought I might be able to remount it, **but I'm not sure how to do this safety, as I do not have physical access to the machine**, and only have terminal access (I have a VNC server set-up, but it's a pain to use for me).

What can I do?

Thanks and best regards,
Cameron.

how is the filesystem been mounted?
```

mount -l

```
also the fact that you cannot read sudo it makes me sospicius about your users priviledges. what is the output for:
```

ls -l /var/lib/sudo/rtorrent

```
also
```

groups $(whoami)

```

ps: put the output in different code tags not all toghether in out. Follow my style/order please.

---

### Post by Pjotr123 on 2013-01-07
Contact the admin who does have physical access to this particular machine, and tell him to upgrade as soon as possible to a supported Ubuntu version. 

Maverick 10.10 is long dead and buried, so it doesn't get security updates. This is very dangerous, also in Linux. You run unacceptable risks with data you put on that system....

---

### Post by fdrake on 2013-01-07
> **Pjotr123 said:**
> Contact the admin who does have physical access to this particular machine, and tell him to upgrade as soon as possible to a supported Ubuntu version. 

Maverick 10.10 is long dead and buried, so it doesn't get security updates. This is very dangerous, also in Linux. You run unacceptable risks with data you put on that system....

+1

But first before you do that I'd like to understand what's the reason of the permission problem..
:p:D:)

---

### Post by rnerwein on 2013-01-07
> **fdrake said:**
> +1

But first before you do that I'd like to understand what's the reason of the permission problem..
:p:D:)
hi fdrake
i agree - just say new installation is a too easy answer ( similar threads in brand new releases).
here my hint: if the root-filesystem is mounted read-only have a look on your /etc/fstab and you will find:
 UUID=2d7726aa-e04a-4265-b5b9-a5cce53b46e2 /         ext3  [COLOR=Red]errors=remount-ro[/COLOR] 0 1
then have a look in /var/log/syslog - kernlog - boot.log (i guess syslog).
i think with only a update the problem isn't gone !
cheers  :-)

---

