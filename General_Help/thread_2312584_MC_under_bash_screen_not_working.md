---
title: "MC under bash screen not working"
date: 2016-02-05
forum: General Help
---

### Post by sohlinux on 2016-02-05
Hello, If I launch MC (midnight commander) under bash screen command its impossible to use any of the F keys and menus. does anyone know why it doesnt work and how to fix it? thanks

---

### Post by ajgreeny on 2016-02-05
What do you mean by  "under bash screen command"?

I assume you are talking of a terminal command to start it, but can you confirm that is so.

---

### Post by sohlinux on 2016-02-05
> **ajgreeny said:**
> What do you mean by  "under bash screen command"?

I assume you are talking of a terminal command to start it, but can you confirm that is so.

yes I mean if I open a terminal then type screen then type mc the menus and F keys dont work.

---

### Post by howefield on 2016-02-05
Working fine on this machine, which version of Ubuntu are you using ?

---

### Post by sohlinux on 2016-02-05
Ubuntu Server 14.04.3

---

### Post by oldos2er on 2016-02-05
Does mc work correctly if you don't run it under screen?

---

### Post by sohlinux on 2016-02-05
yes it works fine without screen but I like to have a many screens running doing various tasks like ftp but it will not work :(

---

### Post by matt_symes on 2016-02-05
Hi

Have you edited screen's configuration files ?

Are you connecting to the server remotely using ssh, vnc or something similar ?

Is the server running in a VM ?

Kind regards

---

### Post by sohlinux on 2016-02-06
I reset screen's configuration files to default and now its working so maybe it was something I edited. thanks

---

### Post by matt_symes on 2016-02-06
Hi

> **sohlinux said:**
> I reset screen's configuration files to default and now its working so maybe it was something I edited. thanks

Excellent. I'm glad it's fixed.

Please mark this thread as SOLVED using the thread tools menu above post #1. It'll help others looking for similar information.

Kind regards

---

