---
title: "Eclipse Console"
date: 2006-11-22
forum: General Help
---

### Post by Quaker on 2006-11-22
Hi!!! I'm programing c in eclipse but in that program i need to create a raw socket wich is a problem because when i run it eclipse send's an error message teling me that i need to be sudo to run that program. 
I've tried to start eclipse as - > sudo eclipse <- it still doesn't work. 
Does anyone know how to run eclipse console as sudo, or if it possible to run the eclipse console as root. 
I could run eclipse in the root acount but i'm trying to avoid it... can anyone help me???

---

### Post by ebash on 2006-11-24
I guess that you are trying to bind a port number below 1024, these ports can only be binded by root. If you can, change the port number that you are using. 

I don't think that you can run the console as root, what you can maybe do is to run your program with sudo but I don't know how. A hack that works, consists on finding the executable that Eclipse produces and changing it's owner ship to root and setting the 's' bit on it. When the executable will be run it will be run as root.

Do the following:
```

sudo chown root ~/Eclipse/Workspace/test-c/Debug/test-c
sudo chmod u+s ~/Eclipse/Workspace/test-c/Debug/test-c

```

I am not sure that you will be able to run the code through the debuger.

---

