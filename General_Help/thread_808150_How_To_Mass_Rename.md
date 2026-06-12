---
title: "How To Mass Rename ??"
date: 2008-05-26
forum: General Help
---

### Post by igmox on 2008-05-26
hi 
i've thousands of .pdf files in a folder and i want to mass rename all these .pdf files according each one's creation date and hour like :

f000000001.pdf -----> 2007-05-25-1457.pdf

i tried many ways but couldn't manage.

i appreciate any help. 10x

---

### Post by bwhite82 on 2008-05-26
For stuff like this, I consult the gurus in the Debian channel on freenode. Its usually some simple, arcane command which was popular when Unix was first made.

---

### Post by igmox on 2008-05-26
yeah, i tried many of those commands but none worked :)

---

### Post by bwhite82 on 2008-05-26
> **igmox said:**
> yeah, i tried many of those commands but none worked :)

Trust me, they'll know. Fire up XChat and go and ask them. Be respectful however, and no need for pre-question chat, just go in and ask your question then wait.

---

### Post by bingoUV on 2008-05-26
backup your files, and then run
```

for i in `ls *.pdf`; do
    mv $i `date -r $i +%Y-%m-%d-%H%S`.pdf
done;

```

Pray to god that no 2 files were last modified on the same second. Note that this is not creation time, but last modification time. Ubuntu does not store creation time.

---

### Post by strabes on 2008-05-26
gprename and pyrenamer may do what you're trying to do.

---

### Post by decoherence on 2008-05-26
This command assumes all your PDFs are in one folder. In the terminal, cd to the folder and enter

for i in *.pdf; do mv $i `ls -l $i | awk '{ print $6 "-" $7 ".pdf"}' | sed 's/://g'`; done

You should run this command on a copy of of the folder just in case I got something wrong and stuff gets clobbered.

Like the above command, this works on modification times, not creation times so it might not be useful.

---

### Post by crossedout on 2008-05-26
Take a look at gthumb.  It's in the repos.

-Xout

---

### Post by Rizlaaf on 2008-05-26
Krename

---

### Post by fsmithred on 2008-05-26
ThunarBulkRename (came with xfce4)

---

### Post by disturbedite on 2008-05-26
i use gwenrename.  it works great & is simple to use yet flexible with lots of options.

---

### Post by igmox on 2008-05-26
> **bingoUV said:**
> backup your files, and then run
```

for i in `ls *.pdf`; do
    mv $i `date -r $i +%Y-%m-%d-%H%S`.pdf
done;

```

Pray to god that no 2 files were last modified on the same second. Note that this is not creation time, but last modification time. Ubuntu does not store creation time.

thank you all, the best solution was bingoUV's suggestion hence it only consists of files' own specifications, other programs in repos keep adding and adding the modified date each time they're run.  

so simple and successful, thank you bingoUV

---

