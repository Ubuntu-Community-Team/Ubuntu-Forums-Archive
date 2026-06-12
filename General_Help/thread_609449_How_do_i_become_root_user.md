---
title: "How do i become root user"
date: 2007-11-11
forum: General Help
---

### Post by kxr1der on 2007-11-11
Im trying to create a file in the /usr/ directory but only the root user can. It says i cant logon to the root user from the login screen so how do i do it?

---

### Post by taurus on 2007-11-11
You can do that with the sudo command.

```
sudo mkdir /usr/**directory_name**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kxr1der on 2007-11-11
thanks that worked, so now how do i move a file into that folder

---

### Post by kd7swh on 2007-11-11
sudo is the safest method, but you can type:

```
su
```

to become root in the terminal. Be careful though, root is all powerful.

---

### Post by taurus on 2007-11-11
```
gksudo nautilus
```

---

### Post by kd7swh on 2007-11-11
to move files

```
sudo mv file1 /to_folder
```

```
 gksudo 
```
is a graphical sudo

nautilus being the file manager

```
gksudo nautilus
```  

is a graphical file manager as root

---

### Post by kxr1der on 2007-11-11
ok this is my last question, i cant find my mozilla directory, where is it usually located, along with the rest o my applications actually?

---

### Post by PmDematagoda on 2007-11-11
The mozilla directory is hidden, press Ctrl+H while in Nautilus to allow hidden files to be seen.

---

### Post by mcduck on 2007-11-11
> **kxr1der said:**
> ok this is my last question, i cant find my mozilla directory, where is it usually located, along with the rest o my applications actually?

Mostly your applications are in /usr/share. But it's not like in Windows where all files of a single application are in the same directory. Instead in Linux all files of the same type, from all applications, are put in one place. So you'll find the executables in /usr/bin, documents in /usr/share/doc and so on.

To find all places where a program has it's files you can use the 'whereis'-command. For example 'whereis firefox'.

---

### Post by mcduck on 2007-11-11
> **kd7swh said:**
> sudo is the safest method, but you can type:

```
su
```

to become root in the terminal. Be careful though, root is all powerful.
BY the way, that won't work in Ubuntu. Su would need root's password, and as long as the root user hasn't been enabled you don't have one..

Use 'sudo -i' and your own password instead if you need to open a root session. 'sudo su' would also work, but that doesn't load rot's environment correctly so it's better to use 'sudo -i' instead.

---

