---
title: "shell server chat?"
date: 2013-03-28
forum: General Help
---

### Post by conradin on 2013-03-28
Hi all, 
I have several users on a shell server. Is there any programs that allow users to chat with other users on the server?
I don't want to use on-line services.

---

### Post by hectorgrebbell on 2013-03-28
Don't know of existing tools, I expect the exist

 As part of a university assignment I had to write a very basic chat client. Theres a piece of code which you run permanently. This receives and displays messages received.
Then another bit of code that broadcasts a message.
It uses multicasting.
You would set up an aliat so youd type 'chat message' into the shell
Any listeners then print the date, the username then the message.

If you'd like i can dig it out for you?

---

### Post by tgalati4 on 2013-03-28
```
man wall
man write
apropos message
apt-cache search chat
```

---

### Post by conradin on 2013-03-29
sounds neat, I would like to check it out!

> **hectorgrebbell said:**
> Don't know of existing tools, I expect the exist

 As part of a university assignment I had to write a very basic chat client. Theres a piece of code which you run permanently. This receives and displays messages received.
Then another bit of code that broadcasts a message.
It uses multicasting.
You would set up an aliat so youd type 'chat message' into the shell
Any listeners then print the date, the username then the message.

If you'd like i can dig it out for you?


I thought about wall, but I'm also looking for recommendations to other programs. write looks good.

---

### Post by CaptainMark on 2013-03-29
If I understand your post correctly you're looking for a terminal based instant messenger, is that correct? If so then install finch, its in the standard repos so can be installed with a quick ```
 sudo apt-get install finch
```its bascially a terminal based version of pidgin so if you use the bonjour protocol, you can make up any username and leave the rest of the settings as they are and that will allow you to chat to anyone on the same local network

---

### Post by oldos2er on 2013-03-29
talk? Never used it myself, but it seems it would do what you want.

---

