---
title: "More gcc problems"
date: 2007-04-07
forum: General Help
---

### Post by Intruder on 2007-04-07
trying to re-install verlihub on a m8's machine via ssh and as usual gcc 4 wont work with it so i thought no probs will use gcc3.3  which would work but even though he is root i cant run this command

andrew@hub:~/verlihub$ CXX=g++-3.3 ./configure
./configure: line 1182: config.log: Permission denied


Anyone have any tips why it wont let me as it will on my server via ssh, cant run the command as root (sudo )  :( 

Cheers for any help 

Int

---

### Post by Famicommie on 2007-04-07
have you tried switching to root user mode with "sudo -i"?

---

### Post by Intruder on 2007-04-07
No i had not and it worked a treat THANK YOU for the quick and helpful reply mate :) 

Int

---

