---
title: "Make a batch file on linux?"
date: 2016-05-05
forum: General Help
---

### Post by peter244 on 2016-05-05
Sorry for extreme noobishness, I only installed Ubuntu today for my friend on is laptop to run a minecraft server for him (I ran it on Ubuntu to maximize the resources the server could use). On Windows 10 to run the server with an allocated amount of RAM (512MB is the Java default I think?) you have to use a batch file which contains this:

```
java -Xms2G -Xmx2G -jar minecraft_server.1.9.2.jar nogui
```

I want to do the exact same thing on Ubuntu 16.04 LTS. How would one go about that? I've tried to use many guides before on this but I always end up getting:

```
Unable to access the jarfile minecraft_server.1.9.2
```

Additional information: The server is vanilla running 1.9.2. The server files are located at /home/peter/Desktop/ms

Thanks in advance for your help!!

---

### Post by jim_deadlock on 2016-05-05
Does this work?

```
cd ~/Desktop/ms
java -Xms2G -Xmx2G -jar ./minecraft_server.1.9.2.jar nogui &

```

---

