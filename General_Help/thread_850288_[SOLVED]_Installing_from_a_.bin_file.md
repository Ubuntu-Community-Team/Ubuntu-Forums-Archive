---
title: "[SOLVED] Installing from a .bin file"
date: 2008-07-05
forum: General Help
---

### Post by Dyffo on 2008-07-05
Have downloaded two software packs - both are .bin files - how do I install these on my system:confused:

---

### Post by pytheas22 on 2008-07-05
Where did you get the software from and what is it?  Is it for Linux or another operating system?  If it's for Linux, you probably just need to copy it into the appropriate directories.  But please provide more information about the software.

---

### Post by Vivaldi Gloria on 2008-07-05
> **Dyffo said:**
> Have downloaded two software packs - both are .bin files - how do I install these on my system:confused:

What software are these? Aren't they available in synaptic or medibuntu? You know that synaptic is the preferred method of installing programs, right?

How to install a .bin file can change from file to file. Look if there are installation instructions. Sometimes double-clicking on them works. If not, you can try installing it as follows:

1) Open a terminal and go to the folder where the file is:

```
cd /where_the_file_is
```

2) make the file executable:

```
chmod +x filename
```

3) Install it:

```
./filename
```

You may need to put sudo before the commands if superuser privilages are needed.

---

### Post by steveneddy on 2008-07-05
> **Vivaldi Gloria said:**
> What software are these? Aren't they available in synaptic or medibuntu? You know that synaptic is the preferred method of installing programs, right?

How to install a .bin file can change from file to file. Look if there are installation instructions. Sometimes double-clicking on them works. If not, you can try installing it as follows:

1) Open a terminal and go to the folder where the file is:

```
cd /where_the_file_is
```

2) make the file executable:

```
chmod +x filename
```

3) Install it:

```
./filename
```

You may need to put sudo before the commands if superuser privilages are needed.

That's exactly what i was going to say.

Many people forget to make it executable.

---

### Post by Dyffo on 2008-07-05
Software is download for Linux from Afterdawn and is emule and Shareaza

---

### Post by Vivaldi Gloria on 2008-07-05
> **Dyffo said:**
> Software is download for Linux from Afterdawn and is emule and Shareaza

There is amule for linux in synaptic. I'm using it and it's quite close to emule. Have a look at it.

I don't know anything about the other software you mention.

---

