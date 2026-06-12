---
title: "How to edit a file?"
date: 2007-07-20
forum: General Help
---

### Post by Tprice on 2007-07-20
Hey all im new to ubuntu so sorry for asking!

Ok i would like to know how to edit a file the the command prompt.

For example i want to edit this file "/etc/network/interfaces" but i dont know what the command is to edit it! How can i get to the point where i can change the files values?

Thanks!

---

### Post by nichipet on 2007-07-20
There are various tools. I would recommend gedit. Since it is a file in /etc you probably want to use:

```
sudo gedit /etc/network/interfaces
```

That will open the interfaces file in gedit and you can change the contents. Being in /etc, you definitely want to back up the file first.

```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
```

would suffice.

If you want to stay in the command line the entire time, you could use emacs, nano, or vim. I'm not in Ubuntu right now, but I assume there's a man (manual) file or a --help option for each of them. Try man vim, man emacs, etc. There are also plenty of tutorials online for all of them.

---

### Post by Tprice on 2007-07-20
> **nichipet said:**
> There are various tools. I would recommend gedit. Since it is a file in /etc you probably want to use:

```
sudo gedit /etc/network/interfaces
```

That will open the interfaces file in gedit and you can change the contents. Being in /etc, you definitely want to back up the file first.

```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
```

would suffice.

If you want to stay in the command line the entire time, you could use emacs, nano, or vim. I'm not in Ubuntu right now, but I assume there's a man (manual) file or a --help option for each of them. Try man vim, man emacs, etc. There are also plenty of tutorials online for all of them.

hey thanks for the help now i can edit files!

But how do i save the file? i have changed what i want but i dont know who to save it!

Can someone help?

---

### Post by Seisen on 2007-07-20
Just click where it says save in gedit.

---

### Post by Tprice on 2007-07-20
Were does it say save? 

PS: i am doing this though the command prompt!

---

### Post by Seisen on 2007-07-20
Then are using vim or something else?

---

### Post by Tprice on 2007-07-20
yes i am using "vim"

So to get into the file to edit it i do this:

```
sudo vi /etc/network/interfaces
```

Then i change the file to what i want.

then what should i do to get out of the stage were i change the file?

---

### Post by Seisen on 2007-07-20
Hit the Escape key then
```
:wq
``` this will save the file and quit.

---

