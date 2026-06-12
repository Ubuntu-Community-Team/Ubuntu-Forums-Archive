---
title: "Executing Binary Files"
date: 2008-07-06
forum: General Help
---

### Post by amtur_poet on 2008-07-06
I have recently downloaded some programs for linux that are in .bin format. I click on them, and it says there is no program to open the file. How do I execute a .bin file in Ubuntu 8.04?

---

### Post by tech0007 on 2008-07-06
cd to the directory, then run 'chmod +x [filename]'.

---

### Post by nvteighen on 2008-07-06
1. Open a terminal (Applications->Accesories).
2. Use "cd" to change directory
3. Type:
```

./application.bin

```

That will work if you have permissions to execute the file. If you don't have them, use "chmod a+x application.bin" if the file is yours. If not, you'll need root privileges.

---

