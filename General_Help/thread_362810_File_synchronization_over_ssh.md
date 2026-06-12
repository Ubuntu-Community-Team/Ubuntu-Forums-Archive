---
title: "File synchronization over ssh"
date: 2007-02-16
forum: General Help
---

### Post by stupid head on 2007-02-16
Is there a program that allows me to synchronize a local directory with a remote directory over SSH? I'm looking for something like the synchronization features in WinSCP and CyberDuck.

What I want to do is keep my computer synchronized with the files in my school shell account. Obviously, I can't use Unison because that requires a process on the server. I don't want rsync because that's a mirroring tool. Version control is too complex. I just want a program that will compare the timestamps and copy over the newer or nonexistent files.

---

### Post by jazzgossen on 2007-02-16
> **stupid head said:**
> I I just want a program that will compare the timestamps and copy over the newer or nonexistent files.
But that's just what rsync does, isn't it?

---

### Post by stupid head on 2007-02-16
> But that's just what rsync does, isn't it?

Yeah, but it's only one-way right? I want the program to see whichever one is newer and replace the older one.

---

### Post by jamesjrl on 2007-02-16
I use a program called unison
it dont beleive it is being maintained anymore, but is (was?) in the ubuntu repository
i've never had any success getting it to work on windows though.

it actually runs as a service you connect to, so is quite fast at checking for newer file versions on the remote side.

---

### Post by stupid head on 2007-02-16
Unison requires that it runs on both the server and client, right? That's out of the question. I tried it anyway and it doesn't work.

---

### Post by jazzgossen on 2007-02-19
> **stupid head said:**
> Yeah, but it's only one-way right? I want the program to see whichever one is newer and replace the older one.

Running rsync twice should fix that, if that's an option.

rsync -u local-directory remote-directory
rsync -u remote-directory local-directory 

The -u (or --update) tells rsync to only update, that is, to skip files that are newer at the destination.

---

### Post by stupid head on 2007-02-28
Thanks, rsync -u will do what I want it to do. I struggled to get this working because it's confusing. I didn't understand why I couldn't rsync over ssh until I played around in a terminal. Nautilus and OpenSSH use SSH locations differently. After I added a colon, it worked. Now I'm using Grsync and its sessions feature.

---

