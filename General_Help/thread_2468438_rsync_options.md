---
title: "rsync options"
date: 2021-10-29
forum: General Help
---

### Post by mrgoodbytes2 on 2021-10-29
Hello guys,

I would like to ask you about some options available for rsync.

I am dealing with a huge amount of data that are been generated in a cluster. The data are structured by time steps storing .gz files like this example,

0.01/{A.gz,B.gz,C.gz}
0.02/{A.gz,B.gz,C.gz}
0.03/{A.gz,B.gz,C.gz}
0.04/{A.gz,B.gz,C.gz}

Normally, I use the following command to download the files,

rsync -avz name@adress:~/folder/0.0* ./

But, as you can see, I download all files A.gz,B.gz,C.gz. I would like to ask if there's a way to download, from all folders 0.0*, just the file A.gz for instance.

---

### Post by ActionParsnip on 2021-10-29
```

0.0[1-9]/{A.gz,B.gz,C.gz}

```

Maybe....or something like that

---

### Post by The Cog on 2021-10-29
You can put wile cards in the middle of strings like this:
```
rsync -avz name@adress:~/folder/0.0*/A.gz ./
```
I think that will work.

---

### Post by sudodus on 2021-10-29
I suggest that you exclude the B and C files, and test it first with the option n 'dry run' to check that you get what you want.

```

sync -avzn --exclude={B.gz,C.gz} name@adress:~/folder/0.0* ./

```

This way you preserve the directory structure (and put the files with the same name into separate directories on the target side).

---

