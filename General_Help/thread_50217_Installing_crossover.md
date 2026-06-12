---
title: "Installing crossover?"
date: 2005-07-19
forum: General Help
---

### Post by dua on 2005-07-19
Hi everyone,

I've just started playing around with Kubuntu today, and having got used to sudo su to get a root terminal and stuff, I'm really liking it!

I'm currently trying to get crossover installed (I can't find a debian package for it, so I'm just trying to do it using the file named install-crossover-standard-demo-4.2.sh) and I can't run the script! (I'm assuming it's a shell script...)

If I try to open it in Konqueror, it tries to open it for me using Kate, which isn't very useful, and I can't find a way of just running it in a terminal. If I try running it in a terminal, whoever I ask to do it (root or my normal user) it says:

dua@transport-3:~/installs$ ./install-crossover-standard-demo-4.2.sh
bash: ./install-crossover-standard-demo-4.2.sh: Permission denied

ls -l tells me:
-rw-r--r--  1 dua dua 12946758 2005-07-19 15:04 install-crossover-standard-demo-4.2.sh

Can anyone shed any light on my confusion?

---

### Post by Dragonmantank on 2005-07-19
You can either set 'Execute' permission on the file by right-clicking and going to 'Properties', or doing a 'chmod a+x <filename>' and then running it

---

### Post by bdamon on 2005-07-19
You could also run   sh ./install-crossover-standard-demo-4.2.sh

---

### Post by dua on 2005-07-20
Hi guys, cheers for the advice - I can now at least get the script to run (although only by using sh ./install-blah - for some reason it complains that I have a bad interpreter if I make it executable then try just running it). However, it responds with:
dua@transport-3:~/installs$ sh ./install-crossover-standard-demo-4.2.sh
: command not found-standard-demo-4.2.sh: line 12:
'/install-crossover-standard-demo-4.2.sh: line 75: syntax error near unexpected token `do
'/install-crossover-standard-demo-4.2.sh: line 75: `  for a in $GUESS_MD5_PATH; do

I tried replicating this problem on my machine at home (which now has kubuntu on it as well :-) ) but it's running fine! I have no idea what's different in the two instances, and I've tried redownloading the file in case it's corrupt but it's made no difference...

---

