---
title: "Harddrive Question"
date: 2007-07-08
forum: General Help
---

### Post by BlazinNightSkye on 2007-07-08
I have two separate hard drives one for my OS the other for my saved stuff. I got the second one after i installed Ubuntu and i can access it but i cant use it Everytime i got to access it , it requires my administrative password and states that it is owned by the root user so i cant access its files. How do i change this so all my Useres can access it?

---

### Post by saxin on 2007-07-08
You could try to type this in a terminal:
```
sudo chown -R username /mount_location/
```

Just change username with the name you use, and /mount_location to where the harddrive is mounted to :)

---

### Post by BlazinNightSkye on 2007-07-08
Thanks that worked perfectly

---

