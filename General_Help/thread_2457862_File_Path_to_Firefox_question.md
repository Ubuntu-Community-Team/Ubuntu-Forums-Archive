---
title: "File Path to Firefox question"
date: 2021-02-11
forum: General Help
---

### Post by jmichaels29 on 2021-02-11
To find Firefox web browser to place in the startup applications for a family member, what is the file path to the location of this browser please.

---

### Post by dinkidonk on 2021-02-11
In a terminal run "whereis firefox" :)

---

### Post by jmichaels29 on 2021-02-11
ok, so is this 4 results of 4 different Firefox file locations.  Just curious.

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /etc/firefox /usr/share/man/man1/firefox.1.gz
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by ActionParsnip on 2021-02-11
[https://www.howtogeek.com/686952/how-to-manage-startup-programs-on-ubuntu-linux/](https://www.howtogeek.com/686952/how-to-manage-startup-programs-on-ubuntu-linux/)

---

### Post by jmichaels29 on 2021-02-11
ok, thanks.
I have also discovered that "system monitor" will reveal the path if you scroll over the name of the "processes"

---

### Post by dinkidonk on 2021-02-11
> **jmichaels29 said:**
> ok, so is this 4 results of 4 different Firefox file locations.  Just curious.

The first result of "whereis" is usually the binary/executable.

---

### Post by cmcanulty on 2021-02-11
Your profile and other firefox files are also in
 /home/yournamehere/.mozilla

---

