---
title: "file permissions"
date: 2007-08-10
forum: General Help
---

### Post by muddymind on 2007-08-10
What is the bash command to set a file to be read-only by the owner?

[]

---

### Post by mcduck on 2007-08-10
> **muddymind said:**
> What is the bash command to set a file to be read-only by the owner?

[]

Do you mean that even owner can only read it (which would hardly make senese) or that others can't read it?

To remove read, write and execute right from everybody except the owner you can use this:
```
sudo chmod go-rwx /path/to/your/file
```
(g for group, o for others, -rwx means that it removes read, write and execute rights.)

See "man chmod" for more info

edit: use sudo only if you are not the owner of the file.

---

### Post by muddymind on 2007-08-10
> **mcduck said:**
> Do you mean that even owner can only read it (which would hardly make senese) or that others can't read it?

To remove read, write and execute right from everybody except the owner you can use this:
```
sudo chmod go-rwx /path/to/your/file
```
(g for group, o for others, -rwx means that it removes read, write and execute rights.)

See "man chmod" for more info

Ok... that doesn't make sense... maybe it's better to change it's ownership to root and block writting to everyone else... how can I change the ownership of a file?

---

### Post by mcduck on 2007-08-10
This changes the ownership of a file to root:
```
sudo chown root /path/to/your/file
```
..and then this one removes write right from others:
```
sudo chmod o-w /path/To/your/file
```

---

