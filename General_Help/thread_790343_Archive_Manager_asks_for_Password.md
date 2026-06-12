---
title: "Archive Manager asks for Password"
date: 2008-05-11
forum: General Help
---

### Post by gnarkilljboy on 2008-05-11
I am trying to unrar something using archive manager. A window comes up that says Password:wolverine then it has a spot for a password, but the rar files are not password protected. Any help?

---

### Post by metiosarius on 2008-05-11
> **gnarkilljboy said:**
> I am trying to unrar something using archive manager. A window comes up that says Password:wolverine then it has a spot for a password, but the rar files are not password protected. Any help?

Did you try entering "wolverine" as the password? :D

---

### Post by gnarkilljboy on 2008-05-11
:lolflag: Yes, I did. I had this problem before, so I just transfered to file from my laptop to my pc, which is running windows, in order to open them. I used a jump stick to transfer the files.

---

### Post by metiosarius on 2008-05-11
> **gnarkilljboy said:**
> :lolflag: Yes, I did. I had this problem before, so I just transfered to file from my laptop to my pc, which is running windows, in order to open them. I used a jump stick to transfer the files.

After the transfer and decompression, perhaps you should consider re-compressing the archive...

---

### Post by gnarkilljboy on 2008-05-11
how do I do that?

---

### Post by metiosarius on 2008-05-11
Oh...

I was just saying that once you had it back on Windows where it was uncompressed, you should make a new archive out of it - perhaps this will get rid of the strange password problem...

---

### Post by gnarkilljboy on 2008-05-11
k..thanks. I will try that.

---

### Post by TheJokerV on 2008-05-18
I am having this same problem. Whenever I try to extract a .rar file, archive manger asks for a password. It has gotten rather annoying because I hve to transfer the rar file to my windows box, unpack it and then transfer the file back. Does anyone have any idea whats going on. I'm running gutsy.

---

### Post by N.N. on 2008-05-18
Make sure you have either the [FONT="Courier New"]unrar[/FONT] or [FONT="Courier New"]unrar-free[/FONT] package installed. These packages are located in the multiverse repository and universe repository, respectively, so be sure to have those enabled. (Go to "System" > "Administration" > "Software Sources" -- see also [https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html)).

You can either install one of the packages from the Synaptic package manager or by issuing the following command in a terminal: ```
sudo aptitude install unrar
```

---

### Post by TheJokerV on 2008-05-18
Yea I tried that and it still says that it needs a password

---

### Post by N.N. on 2008-05-18
> **TheJokerV said:**
> Yea I tried that and it still says that it needs a password

Perhaps this is caused by a bug in file-roller, the default graphical front-end to unrar. Try extracting a .rar file from the terminal: [LIST=1][*]Start by opening a terminal and then navigate to the directory where the .rar file is located, e.g. /home/your_username/, by issuing the following command: ```
cd /home/your_username
```
[*]Then, if the .rar file is called test.rar, for instance, type the following command to extract it with unrar: ```
unrar e test.rar
```
[/LIST]

---

