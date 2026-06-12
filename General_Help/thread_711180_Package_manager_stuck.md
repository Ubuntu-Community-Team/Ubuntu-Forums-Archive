---
title: "Package manager stuck"
date: 2008-02-29
forum: General Help
---

### Post by JohnMoriarty on 2008-02-29
I'm not especially competent with Ubuntu/Linux (recent switch from Windows) but am coping with most problems that come up. However...

The updates that my computer picked up this morning seem to have wrecked the update/package system (they seemed to run more slowly than usual but reported no errors). The updates available icon is now permanently on, and when I select 'Show updates' I get a message box "Software Index is Broken" and told to run Synaptic or sudo apt-get install -f.

Synaptic, when run, reports a broken package (GEdit) but when I select reinstall or remove, synaptic disappears. sudo apg-get install -f results in the following
```

~$ sudo apt-get install -f
[sudo] password for johnmoriarty:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Segmentation fault (core dumped)
```

Where do I go from here?

Any help appreciated.

John

P.S. I'm away over the weekend so may not get back too quickly if you reply.

---

### Post by SOULRiDER on 2008-02-29
First of all try
```
sudo aptitude update
code sudo aptitude dist-upgrade
``` and then we'll see what happend.

---

### Post by JohnMoriarty on 2008-02-29
Thank-you SOULRiDER

```
sudo aptitude update
```
appears to have fixed it without producing any error messages.

Thanks again
Now I can go away for the weekend without worrying about it.
John

---

