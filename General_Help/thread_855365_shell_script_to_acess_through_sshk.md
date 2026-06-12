---
title: "shell script to acess through sshk"
date: 2008-07-10
forum: General Help
---

### Post by dapim on 2008-07-10
sshk -i lsdf01
cd /home/asterisk/
ls

i am unable to run this script, why?

---

### Post by brian_p on 2008-07-10
> **dapim said:**
> sshk -i lsdf01
cd /home/asterisk/
ls

i am unable to run this script, why?

What is sshk?

---

### Post by carcdrcdr on 2008-07-10
Do you mean first:
ssh -i lsdf01

Second I do not see you runng any scripts, just changing your directory then displaying  the contents.

Here is an example of writing and running a simple script:
> darksatellite@~% cat >newscript.sh                              
#!/usr/bin/env bash
echo "hello scripting world" 
darksatellite@~% chmod +x newscript.sh                             
darksatellite@~% ./newscript.sh                                    
hello scripting world
darksatellite@~%                                                     

Is that what you need?

---

