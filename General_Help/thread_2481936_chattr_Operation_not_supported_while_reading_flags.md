---
title: "chattr: Operation not supported while reading flags"
date: 2022-12-13
forum: General Help
---

### Post by PDA1 on 2022-12-13
I'm trying to make a file or folder immutable- not being able to be deleted, on a USB stick.

Here's the command I  use- udo chattr -R -i FileName.txt

But the error message returned is this; 

chattr: Operation not supported while reading flags on FileName.txt

The files that are on my hard drive can be changed with errors using chattr commands listed above.

How can I fix this problem?

---

### Post by SHENGTON on 2022-12-14
The chattr command is used to change the attributes of a file or directory on a Linux system. It sounds like you are trying to use this command to make a file or directory on a USB stick immutable, which means that it cannot be deleted.

However, the error message you are getting indicates that the chattr command is not supported for the file or directory you are trying to make immutable. This could be because the file or directory is on a USB stick, which does not support the chattr command.

If you want to make a file or directory on a USB stick immutable, you will need to use a different method. One way to do this is to use the chmod command, which allows you to change the permissions of a file or directory. To make a file or directory immutable, you can use the following command:

```
chmod -R a-w FileName.txt
```

This command will remove write permission from the file or directory, which will prevent it from being deleted. Keep in mind that this will also prevent you from modifying the file or directory in any way, so you will need to be careful when using this command.
I hope this helps! Let me know if you have any other questions.

---

### Post by PDA1 on 2022-12-14
If you want to make a file or directory on a USB stick immutable, you will need to use a different method. One way to do this is to use the chmod command, which allows you to change the permissions of a file or directory. To make a file or directory immutable, you can use the following command:

```
chmod -R a-w FileName.txt
```

This command will remove write permission from the file or directory, which will prevent it from being deleted. Keep in mind that this will also prevent you from modifying the file or directory in any way, so you will need to be careful when using this command.
I hope this helps! Let me know if you have any other questions.[/QUOTE]

Well, I tried the command, and a little "lock" appeared over the file.  However, I could easily delete it by hitting the delete key.

Is there something that's wrong with the command?

Thank you

---

### Post by PDA1 on 2022-12-15
Problem- the stick is formatted for ms dos, so Properties says.  So, it can't be changed using linux commands.

---

