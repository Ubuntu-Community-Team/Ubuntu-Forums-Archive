---
title: "Synaptic"
date: 2008-02-08
forum: General Help
---

### Post by murilstone on 2008-02-08
i tried to install lm-sensors and got a large update at around the same time, so im not sure what caused the problem, but now when i try to start Synaptic i get this error:

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

thanx for any help...just a thought,  i dont know weather i mess around to much or is Synaptic just fragile?

---

### Post by taurus on 2008-02-08
This is a weird line.

```
/home/root
```
What is your login name, the one you created during the installing process?

```
ls -la /home
```

---

### Post by murilstone on 2008-02-08
ya, i thought "/home/root" was odd also, but i copy/paste right from the error window so i'm sure it is not wrong. 

my login name is "muril"




muril@muril-ubuntu:~$ ls -la /home
total 12
drwxr-xr-x  3 root  root  4096 Feb  6 22:58 .
drwxr-xr-x 21 root  root  4096 Feb  8 09:46 ..
drwxr-xr-x 40 muril muril 4096 Feb  8 11:34 muril

---

### Post by taurus on 2008-02-08
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by murilstone on 2008-02-08
well, as embarrassing as it would have been to have this work...it didnt. it re downloaded, unpacked and set-up almost everything, but when i tried to open snyaptic it gave the same error...

---

### Post by taurus on 2008-02-08
Do you get the same error if you run it from a terminal?

```
gksudo synaptic
```

---

### Post by murilstone on 2008-02-08
yes...

so, what is making it look in "home" shouldn't it be looking in .root ?
is there a way to point it to the correct folder?

---

### Post by murilstone on 2008-02-08
ok, so, i went to  /usr/sbin and clicked on synaptic and it started just fine. does anyone know where the config file is that starts synaptic? im thinking that i may be able to point it to the correct place from there.

---

### Post by ejket on 2008-02-08
> **murilstone said:**
> ok, so, i went to  /usr/sbin and clicked on synaptic and it started just fine. does anyone know where the config file is that starts synaptic? im thinking that i may be able to point it to the correct place from there.

For the time being, you could create a "/home/root" folder and put a symlink in it to "/root/.synaptic" ... then at least things might work until you find out what's going on.  Or more interesting, maybe you'll get another error that might shed some light on things.

---

