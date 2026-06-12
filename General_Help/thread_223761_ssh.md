---
title: "ssh"
date: 2006-07-26
forum: General Help
---

### Post by justin2021 on 2006-07-26
for some reason a friend can't log into the file server i set up. any ideas why? he is using ssh and i opened up all the ports i needed... i think

---

### Post by aysiu on 2006-07-26
"File not found" may mean that it's not there... as opposed to you not having permission to copy it.

---

### Post by justin2021 on 2006-07-26
> **aysiu said:**
> "File not found" may mean that it's not there... as opposed to you not having permission to copy it.

sorry, changed the problem. already posted something like it :) but might you know of any other places where i would have to change the ports besides in the system?

---

### Post by RAOF on 2006-07-26
I assume you've actually got an ssh server installed?  Ubuntu doesn't come with one out of the box :).

If you do, then:
Does your friend have an account on your box he can actually log in to via ssh?  Do you connect to the internet through a router thingy?  Is it set to forward port 22 to your computer?

---

### Post by justin2021 on 2006-07-27
Yes i have ssh installed. I checked my router, but how do i set port 22 to be open on it? its a belkin

---

### Post by RAOF on 2006-07-27
> **justin2021 said:**
> Yes i have ssh installed. I checked my router, but how do i set port 22 to be open on it? its a belkin
I don't know.  Usually they have a administration page you can get to from [http://192.168.1.1](http://192.168.1.1), and have some sort of "port forwarding" page - that's where you need to set it up.  Work out what your IP address is (you should be able to run **ifconfig** from a terminal to get that) and then get the router to forward port 22 to your IP address.

If you don't know, your IP address will look something like **192.168.1.100**, possibly with a different 3rd number, and probably with a different fourth number.

Finally, just to be sure, you have the package **ssh-server** installed? ;)

---

