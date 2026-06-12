---
title: "Insert text from one file into another text file"
date: 2021-04-06
forum: General Help
---

### Post by raleigh3 on 2021-04-06
I would like to be able to insert the contents of a text file at the end of the host file.

I need that because my hosts file is frequently updated.

How can I do that?

Thanks.

---

### Post by SeijiSensei on 2021-04-06
```
cat file1 >> file2
```

Appends the contents of file1 to the bottom of file2. The double redirection (">>") means append. With only one redirection character (">") file2 would overwritten.

---

### Post by raleigh3 on 2021-04-06
It does not work because it is root owned.

I tried

```
echo xx | sudo -S cat AddTo_hosts.txt >> /etc/hosts
```

---

### Post by CatKiller on 2021-04-07
> **raleigh3 said:**
> It does not work because it is root owned.

What you need is for the part of the operation that writes to the file (not necessarily the part that reads from a file) to be run with elevated privileges.

Something like ```
echo 'xxx' | sudo tee -a /etc/hosts
``` or ```
cat AddTo_hosts.txt | sudo tee -a /etc/hosts
```

You can stick a ```
> /dev/null
``` on the end if you don't want the text that you're piping around to also be displayed on your terminal.

---

### Post by raleigh3 on 2021-04-07
Thanks CatKiller.

---

