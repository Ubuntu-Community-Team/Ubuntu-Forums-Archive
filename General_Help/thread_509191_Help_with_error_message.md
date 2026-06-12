---
title: "Help with error message"
date: 2007-07-25
forum: General Help
---

### Post by jrme33 on 2007-07-25
I tried installing updates and got the following message. i also receive it when opening the synaptic package manager. What is it and what do i do? Any help would be greatly appreciated.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Haegin on 2007-07-25
Open a terminal and run "sudo dpkg --configure -a" and paste the output up here (in a code block please).

---

### Post by jrme33 on 2007-07-25
it said the following and then nothing happened......

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

---

### Post by Haegin on 2007-07-25
Sounds like the dpkg run finished fine. Can you now run synaptic and install the updates? Does it work?

---

### Post by jrme33 on 2007-07-25
no. it now says the following...

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by jrme33 on 2007-07-25
i followed the instructions and it now works. i have no clue what caused it though.

---

### Post by Haegin on 2007-07-25
Ok, so now open the terminal again and run "sudo apt-get install -f" and paste the output back here. It sounds like apt has got confused so it needs to force through some packages that it has queued for installation.

---

### Post by Haegin on 2007-07-25
Glad that worked - it was probably apt getting its knickers in a twist. Thankfully it talks you through fixing it pretty well.

---

