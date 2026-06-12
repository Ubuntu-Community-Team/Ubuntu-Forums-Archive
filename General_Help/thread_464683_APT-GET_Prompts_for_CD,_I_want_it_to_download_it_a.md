---
title: "APT-GET Prompts for CD, I want it to download it all, how?"
date: 2007-06-04
forum: General Help
---

### Post by ctaborda on 2007-06-04
Hello,

I'm trying to install apache using apt-get however, it makes me put in the Ubuntu CD, however this server is at a datacenter. I need to be able to install my stuff without putting the cd, how?

Thanks.

Carlos Taborda

---

### Post by phidia on 2007-06-04
I think you need to navigate to the sources.list and comment out the cdrom there. Then run apt-get again.
Hope that helps.

---

### Post by nillzoor on 2007-06-05
Where is sources.list located?

---

### Post by NumberOne on 2007-06-05
```
cd /etc/apt
```

---

### Post by NilsE on 2007-06-05
You can also use the Software Sources in the System menu and just turn it off on the first panel.

---

### Post by taurus on 2007-06-05
```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the line that has CDROM in it to comment it out (usually near the top).  Save it with <Ctrl>o and exit with <Ctrl>x.  

Then, run

```
sudo apt-get update
sudo apt-get install **program_name**
```

---

