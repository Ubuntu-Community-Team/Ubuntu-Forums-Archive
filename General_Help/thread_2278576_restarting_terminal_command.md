---
title: "restarting terminal command"
date: 2015-05-17
forum: General Help
---

### Post by manuleka on 2015-05-17
I know restarting the machine can be:

sudo reboot
sudo shutdown -r
sudo init 6 

What if i just want to restart the terminal program?

Is there a simple command to exit terminal then open it again?

---

### Post by Vladlenin5000 on 2015-05-17
Well... *exit* closes Terminal but AFAIK there's nothing to make it "restart". Why would you want that, may I ask?
The terminal does nothing in itself, commands you enter there do; when the Terminal shows you a user prompt
```
user@machine:~$
```
it's doing nothing but wait for the user's input. Why restart?

---

### Post by manuleka on 2015-05-17
> **Vladlenin5000 said:**
> Well... *exit* closes Terminal but AFAIK there's nothing to make it "restart". Why would you want that, may I ask?
The terminal does nothing in itself, commands you enter there do; when the Terminal shows you a user prompt
```
user@machine:~$
```
it's doing nothing but wait for the user's input. Why restart?

out of curiosity and also sometimes i prefer a fresh terminal rather then a cleared one (clear) which just pushes 'prompt' forward number of lines to hide previous commands/lines

---

### Post by steeldriver on 2015-05-17
Well you could do

```

x-terminal-emulator && exit

```

I guess... make an alias from it if you want a 'simple command'

---

### Post by manuleka on 2015-05-17
> **steeldriver said:**
> Well you could do

```

x-terminal-emulator && exit

```

I guess... make an alias from it if you want a 'simple command'

awesome! :) Sank-You

---

