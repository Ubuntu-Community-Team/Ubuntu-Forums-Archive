---
title: "scripting"
date: 2005-10-04
forum: General Help
---

### Post by desheikh on 2005-10-04
Hey guys,

Iv been experimenting with scripting in linux and been trying to create a script to automate the stuff i install update etc on my kubuntu hoary.. its going along pretty well but theres just one problem.. I want   the script to be just one file.. but right now im using a seperate file to copy over my own sources.list file... so the sources.list file has to be integrated in the script.. only thing is I cant seem to figure out how to write/append text to files from within the script itself.. could someone guide me as to the commands for that? This is how its being done write now...

...
# Modifying sources.list
echo "modifying sources.list"
cp mysource.list /etc/apt/sources.list
${apt} update
check_errs $? "AAAARRGHHH!"
sleep 5
....

Yeah i ripped off a bit from the ubuntu automate script :P..

Thanks,
Ali

---

### Post by dcraven on 2005-10-04
To append text to a file in bash,
```
echo "your text" >> yourfile
```

Cheers,
~djc

---

### Post by desheikh on 2005-10-04
Why are the things that seem the toughest always the easiest to solve :S..
thanks for the reply :D

---

