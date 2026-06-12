---
title: "How can I directly read a directory as a file from Bash?"
date: 2022-03-12
forum: General Help
---

### Post by Paddy Landau on 2022-03-12
***EDIT:** What looked like the file actually isn't, and what I want isn't straightforward.*

I know that a directory is actually a specialised file, e.g. ~/Pictures is actually a file containing details about what's inside the Pictures folder.

I can view the folder-file directly using vim:
```
view ~/Pictures
```
vim gives a warning message, *"~/Pictures/" Illegal file name*, but still allows me to view it.

(Presumably, I would lose data to edit the file, so I won't attempt to do that! Actually, I tried this in a VM to see what would happen, and the system wouldn't let me directly modify it, at least not with Bash or vim.)

I'm curious about how to read that file directly from a Bash script. I tried using this:
```
while read ENTRY
do
        printf '%s\n' "${ENTRY}"
done <${HOME}/Pictures
```
But this doesn't work, because Bash (correctly) returns the error that Pictures is a directory. Likewise, I can't use cat to display the folder-file:
```
$ cat ~/Pictures
cat: /home/paddy/Pictures: Is a directory
```
Is there some command that I can use within a script to directly read the folder-file?

*I know that this is an odd request. I'm asking out of sheer curiosity, not because I need it.*

Thank you &#128522;

---

### Post by ajgreeny on 2022-03-12
Not sure what you mean by "read a directory"..

What sort of content or information do you want to see? You can see what the directory contains with many variations of the _ls_ command but I assume that is not what you're looking for so tell us in more detail what you hope to be able to get from this.

---

### Post by Paddy Landau on 2022-03-12
> **ajgreeny said:**
> Not sure what you mean by "read a directory".
It seems that I didn't quite explain clearly enough.

Remember that a directory is actually a file in Linux. So, ~/Pictures is in reality just a file.

Try for yourself. Issue this command:
```
vim -R ~/Pictures
```
See what happens? You see the contents of the actual file that is Pictures.

That's what I want to access from a script.

---

### Post by Holger_Gehrke on 2022-03-12
Would an array with the file names be O.K. ?
```

declare -a files
files=(*)
#number of files:
echo ${#files
[*]}

```

If you need more than the name about a single file, 'stat' can give that to you. See 'man stat'.

Holger

---

### Post by Paddy Landau on 2022-03-12
> **Holger_Gehrke said:**
> Would an array with the file names be O.K. ?
Unfortunately, you have misunderstood my query.

Open a terminal and enter this command:
```
vim -R ~/Pictures
```
Notice what happens.

That is what I want to be able to access.

---

### Post by HermanAB on 2022-03-12
Try dd and hexedit.

It would be wise to experiment on a test system, such as a Raspberry Pi and not on your main computer.

---

### Post by Holger_Gehrke on 2022-03-12
That's netrw, the file manager module of vim, similar to Emacs' diredit. It's not editing the raw directory. The only thing I can find which actually allows you to play around with the raw data structures of the file system is the [Linux Disk Editor]("https://sourceforge.net/projects/lde/") which is modelled on the old disk editor from the Norton Utilities for DOS.

Holger

---

### Post by dragonfly41 on 2022-03-12
Perchance referring to reading extra folder permissions?

[https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits](https://linuxconfig.org/how-to-use-special-permissions-the-setuid-setgid-and-sticky-bits).

---

### Post by HermanAB on 2022-03-12
Apart from dd and hexedit mentioned above, you can also try gdb.

---

### Post by Paddy Landau on 2022-03-12
> **HermanAB said:**
> It would be wise to experiment on a test system, such as a Raspberry Pi and not on your main computer.
I have a VM, so I'll experiment there :)
> **HermanAB said:**
> Try dd and hexedit.
dd and hexedit both complained about it being a directory.
> **Holger_Gehrke said:**
> That's netrw, the file manager module of vim, similar to Emacs' diredit. It's not editing the raw directory.
Ah, this is interesting, thank you. In other words, you're telling me that vim isn't actually looking at the file, but instead is reporting it in a useful format?
> **Holger_Gehrke said:**
> The only thing I can find which actually allows you to play around with the raw data structures of the file system is the [Linux Disk Editor]("https://sourceforge.net/projects/lde/") which is modelled on the old disk editor from the Norton Utilities for DOS.
I had a look, but I don't know how to install this :(
> **dragonfly41 said:**
> Perchance referring to reading extra folder permissions?
No, that's not what I'm after.
> **HermanAB said:**
> … you can also try gdb.
gdb looks like a debugger for programs. I don't know how to use it for a file.

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

Thank you all for your help.

It looks as though @Holger_Gehrke has it correct, that it's not actually the file that I'm looking at. Instead, vim is interpreting the contents for me, which is not the same thing!

This was a fun experiment, but in the end, it seems that I'm looking for something that is hardly straightforward.

I shall mark this thread as solved, and thank you all again.

---

