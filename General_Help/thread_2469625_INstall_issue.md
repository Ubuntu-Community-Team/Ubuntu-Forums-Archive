---
title: "INstall issue"
date: 2021-12-04
forum: General Help
---

### Post by peter-1984 on 2021-12-04
Hi,
HOw to resolve issue below when running "apt install net-tools"?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289586&stc=1[/IMG]

---

### Post by Frogs Hair on 2021-12-04
This appears to be a temporary error. You can try the suggestions in the terminal or change the server location in software & updates > updates. 

```
sudo apt update --fix missing 
```

---

### Post by peter-1984 on 2021-12-05
I've re-tried and have still got the same problem. Where to change the server location?

---

### Post by peter-1984 on 2021-12-05
I've re-tried and have still got the same problem. Where to change the server location in the following?

---

### Post by tea for one on 2021-12-05
> **peter-1984 said:**
> I've re-tried and have still got the same problem. Where to change the server location in the following?

The server location is not in Settings

Software & Updates > Ubuntu Software > Download from > Click Down Arrow > Make your choice

This was mentioned in post 2

---

### Post by peter-1984 on 2021-12-05
Can you help as I don't see Software & Updates below?

---

### Post by tea for one on 2021-12-05
Are you still using server version as your previous thread?
[https://ubuntuforums.org/showthread.php?t=2469575&page=3&p=14069892#post14069892](https://ubuntuforums.org/showthread.php?t=2469575&page=3&p=14069892#post14069892)

---

### Post by peter-1984 on 2021-12-05
Yes.

---

### Post by tea for one on 2021-12-05
```
sudo apt install synaptic
```

Synaptic will also give you access to server location.

---

### Post by peter-1984 on 2021-12-05
Sorry to that I have issue below (when running the command sudo apt install synaptic)

[https://ubuntuforums.org/attachment.php?attachmentid=289595&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289595&stc=1)

---

### Post by tea for one on 2021-12-06
As you have installed the server version of Ubuntu, you will have to manage your software sources/mirrors via the command line.
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Alternatively, you could back up your data and install Ubuntu Desktop version, where all the GUI utilities will be available.

---

