---
title: "change owner problems"
date: 2007-08-26
forum: General Help
---

### Post by AWerner32 on 2007-08-26
i created an ftp server and made a user to use it with, for some reason the way i did it the home folder of my user i inteded for ftp use is actually owned by my main user. i'm kinda a noob but not that bad and i tried to change the ownership as many ways as i knew how however it always said permission denied. If the owner of the folder can't change the ownership and the root can't then i don't know how to. 

> chown: changing ownership of `/home/user': Operation not permitted
andrew@andrew-playstation:~$ chown user /home/user
chown: changing ownership of `/home/user': Operation not permitted
andrew@andrew-playstation:~$ sudo chown user /home/user
chown: changing ownership of `/home/user': Operation not permitted
andrew@andrew-playstation:~$ chown root /home/user
chown: changing ownership of `/home/user': Operation not permitted
andrew@andrew-playstation:~$ sudo chown root /home/user
chown: changing ownership of `/home/user': Operation not permitted


---

### Post by merlinus on 2007-08-26
You might try this:

```

sudo chown -R username:username /home/username

```

You can also open nautilus as root and try to do it that way:
```

gksudo nautilus

```

-merlin

---

### Post by AWerner32 on 2007-08-26
i had tried the gksudo approach before, doesnt work. and the other approach errors out on all of the files

---

### Post by AWerner32 on 2007-08-27
I solved this problems. Turns out the user that mounts a drive is automatically the owner of all of its contents and you cannot change that while its mounted

---

