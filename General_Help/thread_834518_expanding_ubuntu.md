---
title: "expanding ubuntu"
date: 2008-06-19
forum: General Help
---

### Post by jnw222 on 2008-06-19
ok, i was trying ubuntu on a Toshiba satelite L35 with vista preinstalled
and then i changed the partitions a little for a dual boot with hardy
now i want ubuntu on the hard drive and no other os 

i need a step-by-step tutorial

---

### Post by russlar on 2008-06-19
step 1: download the gparted live cd from [here]("http://gparted.sourceforge.net/livecd.php")

step 2: boot to the live cd downloaded in step 1

step 3: launch gparted (it's a gui)

step 4: delete the vista partition

step 5: expand the linux partition into the free space

step 6: profit.

---

### Post by jnw222 on 2008-06-19
i do not feel so comfortable with expanding it to the left (espically after what happened last time

---

### Post by russlar on 2008-06-19
> **jnw222 said:**
> i do not feel so comfortable with expanding it to the left (espically after what happened last time

what happened last time?

---

### Post by jnw222 on 2008-06-19
what about the gnome partition editor that i used for the screenie (downloadable from supported apps under add/remove apps

---

### Post by jnw222 on 2008-06-19
last time i used it to meve/expand it left, it crahsed and all data was unreadable

---

### Post by russlar on 2008-06-19
> **jnw222 said:**
> what about the gnome partition editor that i used for the screenie (downloadable from supported apps under add/remove apps

that is the program you use, you just need to have the root volume not mounted, which cannot be done unless running from a live cd.

---

### Post by jnw222 on 2008-06-19
oh and last time it was another partition

---

### Post by russlar on 2008-06-19
honestly, backup your system, boot to a live cd, and give it a shot. I used a knoppix disc to do an identical procedure on my T61. It took a couple of hours, but it ran no problems, no errors, and no corruption.

---

### Post by jnw222 on 2008-06-19
would formating the vista partition to ext3 and then copying all files over work

---

### Post by russlar on 2008-06-19
> **jnw222 said:**
> would formating the vista partition to ext3 and then copying all files over work

not really, you'd still have two separate partitions.

---

### Post by Deutscher Alex on 2008-06-19
> **russlar said:**
> honestly, backup your system, boot to a live cd, and give it a shot. I used a knoppix disc to do an identical procedure on my T61. It took a couple of hours, but it ran no problems, no errors, and no corruption.

heh i tried installing knoppix to duel boot with vista, totally screwed up my system. So I had to install ubuntu, and I still can't boot vista anymore....

I'd say give russlar's method a shot.

---

### Post by russlar on 2008-06-19
> **Deutscher Alex said:**
> heh i tried installing knoppix to duel boot with vista, totally screwed up my system. So I had to install ubuntu, and I still can't boot vista anymore....

i didn't know installing knoppix was possible...

---

