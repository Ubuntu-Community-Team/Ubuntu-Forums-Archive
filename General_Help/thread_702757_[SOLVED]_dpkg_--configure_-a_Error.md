---
title: "[SOLVED] dpkg --configure -a Error?"
date: 2008-02-20
forum: General Help
---

### Post by NeonOnion on 2008-02-20
Where do I run to fix it?

Super dumbed down replies please,
I'm not too good at this.

Oh and someone please stick around to help?
Every time I have a problem with Ubuntu,
I seem to have tons more fallowing..

---

### Post by sisco311 on 2008-02-20
open a terminal:

Applications -> Accessories -> Terminal


type:
```
sudo dpkg --configure -a
```

type your password.
press Enter

---

### Post by NeonOnion on 2008-02-20
I got this message (I changed my password though).

neononion@neononion:~$ sudo dpkg --configure -a
neononion@neononion:~$ password
bash: password: command not found
neononion@neononion:~$

---

### Post by NeonOnion on 2008-02-20
Eekies..Um..Boost Up My Post..?

---

### Post by NeonOnion on 2008-02-20
So I kept trying to use it
And now I'm getting this;;

neononion@neononion:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
neononion@neononion:~$ 


Aren't I the superuser?
I typed in my password and it told me the command wasn't found..

---

### Post by sisco311 on 2008-02-20
type
```
sudo dpkg --configure -a
```this command will promt you for your password:

> [sudo] password for neononion:type your password and press Enter.

---

### Post by NeonOnion on 2008-02-20
Ubuntu is really starting to piss me off.. ._.;

It doesn't ask me for my password.
It just keeps giving me my screen name..

---

### Post by sisco311 on 2008-02-20
it's ok. open Synaptic Package Manager and press the Reload button.

---

### Post by ahsile on 2008-02-20
> **NeonOnion said:**
> Ubuntu is really starting to piss me off.. ._.;

It doesn't ask me for my password.
It just keeps giving me my screen name..

The "sudo" command will only ask you for your password every few minutes so that you don't need to keep typing it again and again. If you run a command with sudo and it doesn't ask you for your password then it means that you've already done it recently.

---

### Post by NeonOnion on 2008-02-20
Alright, then what?

---

### Post by NeonOnion on 2008-02-20
Oh alright, thank you.
I have a short temper, sorry.
=^^;=

---

### Post by NeonOnion on 2008-02-20
So to stop my confusion more,
is the Update Manager 
the same thing as the Synaptic Package Manager?

---

### Post by ahsile on 2008-02-20
The update manager is a little different from Synaptic Package Manager. Synaptic is for adding and deleting programs. The update manager is for security updates to the programs you already have installed.

---

### Post by NeonOnion on 2008-02-20
Ah.
Well the Update Manager is where the error is showing up,
not the Synaptic Manager..

---

### Post by sisco311 on 2008-02-20
run this command from the terminal:

```
update-manager
```

and update your system.

---

### Post by NeonOnion on 2008-02-20
Alright..Loading..

---

### Post by NeonOnion on 2008-02-20
Thanks!
I think it's all fixed now.
=^^= <3<3

---

