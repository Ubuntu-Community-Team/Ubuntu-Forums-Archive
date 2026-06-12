---
title: "Help with scp command"
date: 2021-10-01
forum: General Help
---

### Post by flox1991 on 2021-10-01
Hello,
Basically I need to get a file that is in a certain folder of an ubuntu virtual server (to which I have access) to have it on my own machine. my login on the serv is user1
So I use :
scp /pathwayofthefile.txt user1@myip:/home/arnaud (the personal folder where I want to get it)


It asks me the access pass to the server and then it puts me "/home/arnaud" is a directory.


I'm a beginner so I hope I've been clear enough. It would be great if someone could help me. Thanks

---

### Post by guiverc on 2021-10-01
Assuming *arnaud* is your user account - yes that is a directory.  My own user directory is /home/guiverc/ with my files within that directory.

Your command doesn't tell it to save the file in that directory; but overwrite the directory itself with the contents of that file; which I'm betting wasn't your intention (it gave an error protecting your data).

Why not use **/home/arnaud/file.txt** (of whatever filename you prefer) ie. save the file to "file.txt" inside the directory /home/arnaud/

---

### Post by Impavidus on 2021-10-01
On which computer are you running that command? Your own or the server?

The first argument of scp is the source (where you want to copy from), the second is the destination (where you want to copy to), but then you say that your login on the server is user1, which you use in the second argument, indicating that you want to copy to the server. Is myip your own computer or the server?

---

