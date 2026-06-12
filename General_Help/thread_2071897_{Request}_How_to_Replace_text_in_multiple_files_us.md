---
title: "{Request} How to: Replace text in multiple files using 'SMBTREE -Nb' as source text"
date: 2012-10-16
forum: General Help
---

### Post by Tilde88 on 2012-10-16
Hi all!
 Well, though I am slightly familiar with seb, echo, cat and whatnot... I need some insight. Here's the scenario:
 I will be administrating multiple machines as their backup operator. This said, each machine has to be setup individually. This isn't too much a problem, except for the fact that I need to use the PC's hostnames (or IPs but I would prefer hostnames in order to keep the .sh files named accordingly). What I would like to do, is have some sort of script which would run "smbtree -Nb", which I'm sure you know will list all the computers on the current network. Now how would I be able to use the listing that SMBTREE gives as a source to modify a multitude of files. 
IE, smbtree -Nb gives out
>    //PC1
          //PC2
          //PC3
How can I make PC1 into $1 (relative line 1) so that the script can then insert $1 into the existing document which reads "$BOX=[SIZE="1"]blank[/SIZE]". I want it to change that into "$BOX=PC1" for the first .sh. Then for the 2nd .sh, I want that one to readout "$BOX=PC2" and so on and so forth. 
 Sorry for making this sound so convoluted, I just don't know how else to phrase is.
 Additionally, if you could also help with the renaming of the .sh files, to read their respective replaced text as their actual filename. 

 Thank you all in advance, and again, my apologies in any confusion arises.

---

### Post by Tilde88 on 2012-10-17
Bump. Please advise :\

 TIA :)

---

### Post by Vaphell on 2012-10-17
```
$ ls
script.template
$ cat script.template
#!/bin/bash
box=host
$ for h in //PC1 //PC2 //PC3; do sed "/box=host/ s/host/${h#//}/" script.template > "${h#//}.sh"; chmod +x ${h#//}.sh; done
$ ls
PC1.sh  PC2.sh  PC3.sh  script.template
$ cat *.sh
#!/bin/bash
box=PC1
#!/bin/bash
box=PC2
#!/bin/bash
box=PC3
```
i used hardcoded values in the example (for h in host1 host2 host3; do ...; done) but when you need to use the output of any command, *while* loop is better
```
while read -r h; do ...; done < <( smbtree -Nb )
```

another approach would be to have only 1 parametrized script that does the main thing ($1 will get substituted by passed value) and a wrapper that shows the list of hosts from the output in the form of interactive menu. Selected value is passed to the main script. Or maybe all is done in 1 script - 1st part fills the variable with select, later parts performs their proper job using that variable.

```
$ hosts=( $( smbtree -Nb | sed 's:^//::' ) )
$ select h in "${hosts[@]}"; do echo we will run \'main_script $h\' now; break; done
1) PC1
2) PC2
3) PC3
#? 2
we will run 'main_script PC2' now

```

---

### Post by Tilde88 on 2012-10-18
o.0 thanks! I will get to work with this very soon! Much much appreciated :)

---

