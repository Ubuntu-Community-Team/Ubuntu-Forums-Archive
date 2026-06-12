---
title: "Aegis Virus Scanner"
date: 2006-12-14
forum: General Help
---

### Post by Deviltongue on 2006-12-14
I installed the Aegis Virus scanner but I can't locate it. can someone help me by telling me how to find it or a Virus Scanner that I could use?
-Deviltongue the TruVisionary

---

### Post by oracle5 on 2006-12-14
I wouldn't use aegis since it returns a lot of false positives. I used it long enough for it to tell almost everything was infected and then I switched to using clamav.

oracle5

---

### Post by drphilngood on 2006-12-14
> **Deviltongue said:**
> I installed the Aegis Virus scanner but I can't locate it. can someone help me by telling me how to find it or a Virus Scanner that I could use?
-Deviltongue the TruVisionary
Enter this in a terminal:
```
aegis-virus-scanner
```

Use ¨gksudo¨ when updating or scanning files requiring root access.

---

### Post by drphilngood on 2006-12-14
> **oracle5 said:**
> I wouldn't use aegis since it returns a lot of false positives. I used it long enough for it to tell almost everything was infected and then I switched to using clamav.

oracle5

I haven´t had any ¨false positives¨ and have nothing but good things to say about aegis.  However, I do like ClamAV, as well.

---

### Post by Deviltongue on 2006-12-15
How do u Install ClamAV?

---

### Post by drphilngood on 2006-12-15
> **Deviltongue said:**
> How do u Install ClamAV?

See here:

[How_to_ClamAV]("http://ubuntuforums.org/showthread.php?t=30060")

edit:
If you want a GUI with that, enter:

```
sudo apt-get install clamtk
```

---

