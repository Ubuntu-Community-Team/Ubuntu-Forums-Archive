---
title: "restricting access to home folder edubuntu client"
date: 2007-10-28
forum: General Help
---

### Post by gnw23 on 2007-10-28
I have installed edubuntu server 7.10 on an intel 2.6 core2 duo processor with intel d945 motherboard and 2 GB ram with 160 GB sata hdd

and i have cliets ranging from celeron 500 to PIII 900 with ram from 128 to 256 mb

but all r intel processors

now i have created users 

like 

trinity

trinity1

trinity12

but when they login as a user on edubuntu clients they can see the home folder and all the other desktop like trinity trintiy1 and trinity2

is there any way in which i can recrict access of trinity to only her desktop and trinity1 to her desktop and trinity12 to her desktop and not the entire home folder of edubuntu server so that no one should mess up the home folder of edubuntu server

Thanx in advance

plz help me with this

---

### Post by taurus on 2007-10-28
You can change the permissions so that only mike has access to his own $HOME only.

```
sudo chmod 700 /home/mike /home/trinity /home/trinity1 /home/trinity12
ls -la /home
```
Now, nobody can access others $HOME.

---

### Post by gnw23 on 2007-10-30
thanx it worked 

thanx again

---

### Post by gnw23 on 2007-11-19
hi 

is there a way to reverse this thing and go back to original settings

since now i want to put these home folders to different PC but there is a problem with the permissions and  owner of this individual folders 

so how can we reverse these settings to its original setting

---

