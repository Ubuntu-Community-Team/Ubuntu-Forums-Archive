---
title: "Nohup output to txt file in ssh"
date: 2019-10-12
forum: General Help
---

### Post by jenniferruurs on 2019-10-12
I am via a ssh connectioned to our Ubuntu server.

There i have python script (named f2.py) that has to run four 2 days every hour there is print statement inside the python file.

Why does this not create a file?:
```
nohup python -u f2.py >> home/jen/nohup.txt &
```

---

### Post by SeijiSensei on 2019-10-12
You're missing the leading / on /home/jen/nohup.txt.  Probably there is no "home/jen" directory under the directory where the script is being executed.

---

