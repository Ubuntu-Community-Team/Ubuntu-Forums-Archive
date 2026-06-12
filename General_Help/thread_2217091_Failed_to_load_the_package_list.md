---
title: "Failed to load the package list"
date: 2014-04-15
forum: General Help
---

### Post by Panawe on 2014-04-15
Hi,

Got the following message today via backend_helper.py ...

   [I]Failed to load the package list 
[/I]
*This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.*
*E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.*

Anybody know what's happening?

---

### Post by Bashing-om on 2014-04-15
Panawe; Hi !

Looks like, from the error message, a damaged control file. Try and remove/rebuild these indexes :
Terminal commands:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
Please to advise on results.

[INDENT]We fix everything
[INDENT][INDENT]broken hearts, takes a while
[/INDENT][/INDENT][/INDENT]

---

### Post by Panawe on 2014-04-16
Many thanks.

---

### Post by Bashing-om on 2014-04-16
Panawe; 

[INDENT]welcome
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ironscf on 2014-08-13
Bashing-om: I tried Synaptic , backend-helper, reboot all gave the same error. Then I found the commands in your post. That fixed the index files and now I see Update Manager needs to download 100Mb to update 28 items.

Next time I will check Ubuntu Forums before wasting a lot of time.  
Many thanks for skilled advice.

---

### Post by Bashing-om on 2014-08-13
@ ironscf   : )

Help and guide and teach, well -> that is what we do.

[INDENT][INDENT]who ya gonna call 
[/INDENT][/INDENT]

---

### Post by Allan_Shillam on 2014-08-18
Thanks for the good advice Bashing-om. I had a similar issue with errors about package headers and your commands fixed it all and updated everything.

I remember watching that movie when it first came out...

---

### Post by Bashing-om on 2014-08-18
Allan_Shillam; Great !

That is one of the better aspects of this forum, such a HUGE storehouse of information. A bit of searching can lead to a whole new world !
Rare indeed is it "something new" .

[INDENT][INDENT]seek and ye shall find
[INDENT][INDENT][INDENT]else:
[INDENT][INDENT][INDENT][INDENT]ask and it shall be given
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

