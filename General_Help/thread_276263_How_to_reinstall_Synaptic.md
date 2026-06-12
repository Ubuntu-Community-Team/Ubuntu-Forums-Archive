---
title: "How to reinstall Synaptic?"
date: 2006-10-12
forum: General Help
---

### Post by Gargamella on 2006-10-12
How to reinstall Synaptic?

i have an error with synaptic:

E: Impossibile analizzare il file dei pacchetti /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.

(the first part says:"impossible to analyse package file ...")

so i think the only way is to reinstall synaptic how should i do this?

waiting for a reply

---

### Post by Kateikyoushi on 2006-10-12
Seems not many ideas how to do this.
Lets see maybe you have a backup of that file.
Copy this to a terminal, and report back the output.

```
ls /var/lib/dpkg
```

---

### Post by ajgreeny on 2006-10-12
It may be that apt is the problem, not synaptic, but try *sudo apt-get install synaptic dpkg* and see what happens.

---

### Post by Kateikyoushi on 2006-10-12
I read a bit about that file. It keeps the status of the system,the intalled packages and can not be rebuilt but, you must have a backup of it called status-old.

---

### Post by Gargamella on 2006-10-13
mmmm ok so here it is the ls:

andrea@andrea-laptop:/var/lib/dpkg$ ls
alternatives   cmethopt        info     parts             status
available      diversions      lock     statoverride      status-old
available-old  diversions-old  methods  statoverride-old  updates

i've seen status-old file,but the question is how much old is it?
because it may be the same thing ...

and can't run apt commands:


andrea@andrea-laptop:/var/lib/dpkg$ sudo apt-get install synaptic dpkg
Password:
Lettura della lista dei pacchetti in corso... Errore!
E: Impossibile analizzare il file dei pacchetti /var/lib/dpkg/status (1)
E: La lista dei pacchetti o il file di status non possono essere letti o aperti.andrea@andrea-laptop:/var/lib/dpkg$


so should i copy the status-old content in status file?

---

### Post by Gargamella on 2006-10-13
i also tried to copy the old status in status file...

nothing

it says after that error to fix broken packages, but i don't know how to do it.

should i reinstall ubuntu?

---

### Post by Kateikyoushi on 2006-10-13
I would back up important data first.
Then try the following to fix the broken packages.

```
sudo apt-get -f install
```

---

### Post by Gargamella on 2006-10-13
andrea@andrea-laptop:~$ sudo apt-get -f install
Password:
Lettura della lista dei pacchetti in corso... Errore!
E: Impossibile analizzare il file dei pacchetti /var/lib/dpkg/status (1)
E: La lista dei pacchetti o il file di status non possono essere letti o aperti.andrea@andrea-laptop:~$


(same error)

---

