---
title: "ssh in 1 line automagically"
date: 2006-10-15
forum: General Help
---

### Post by ser1alsn1per on 2006-10-15
hi 
at the terminal how do i log in to another computer via ssh in 1 line



ie name:host:password    i dont know just a guess 


192.168.1.66:password    another guess 


i know how to use keys but thats not the question

any help would be great

---

### Post by adwait on 2006-10-15
Not possible to type the password one the same line because it would be plainly visible....

---

### Post by RichJacot on 2006-10-15
If your user name is the same on the other host (and your keys are setup) just:

ssh hostname

If your user name is NOT the same on the other host (and your keys are setup) just:

ssh -l username hostname

---

### Post by taurus on 2006-10-15
I think he wants to type everything, including username and password, in one line to log into remote host...

You can use the rhost!!!

---

### Post by buttari on 2006-10-15
There's no way you can type the password embedded in the ssh command. Rhost won't help because it's ssh and not rsh. What you can do is export your key to the host where you want to log in. Let's assume that you want to log into host_b from host_a; from the host_a command line execute (being in you home dir)
```
ssh-keygen -y dsa
```
this will create the files .ssh/id_dsa and .ssh/id_dsa.pub. At this point execute:
```
scp .ssh/id_dsa.pub host_b:
```
type passwd. Then execute:
```

ssh host_b mkdir .ssh
ssh host_b cat id_das.pub >> .ssh/authorized_keys

```
type passwd for both commands.
At this point you are done. If you try to ssh to host_b you should be able to log in without typing the passwd.

alfredo

---

