---
title: "Xampp Not Working?"
date: 2014-06-05
forum: General Help
---

### Post by RCAProduction on 2014-06-05
When I download the xampp file, it is a .run file (Which cannot be run and there are no available applications that can run it)... Everything I have read says it should be a .tar.gz file. I can compress it to a .tar.gz and extract it to the /opt directory, but nothing I have encountered will actually run it... (This includes many terminal codes) Does anyone know what's going??

---

### Post by promet on 2014-11-01
Hi,

Did you try 

```
  chmod a+x 
```
 
to make the file executable?

---

### Post by cybercity@localhost on 2014-11-01
execution command for .run applications should start with bash. become root and try these commands.
```
chmod +x yourfile.run
```
```
bash ./yourfile.run
```
hope it helps.

---

### Post by Alireza_Zamani on 2014-11-01
[http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu](http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu)

---

