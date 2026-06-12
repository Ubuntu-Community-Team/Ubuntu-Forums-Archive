---
title: "Synaptic Package Manager gone!?!?"
date: 2006-10-26
forum: General Help
---

### Post by cabber on 2006-10-26
I'm using Dapper 6.10 and just noticed I cannot pulll up the Synaptic Manager any more.  When I click System/Administration/Synaptic Manager, it asks me for my password and never opens.  Can someone assist with this?  Thanks.

Cabber

---

### Post by PriceChild on 2006-10-26
could you do```
gksudo synaptic
```from the terminal and paste any error here please.

---

### Post by dbott67 on 2006-10-26
Others have reported problems opening Synaptic from the menu.  The workaround (at present) is to open a terminal and type:
```
sudo synaptic
```
-Dave

---

### Post by cabber on 2006-10-26
> **PriceChild said:**
> could you do```
gksudo synaptic
```from the terminal and paste any error here please.

Thank you for your assistance:  Here's the output:

```
chop@chop-dapper:~$ gksudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
chop@chop-dapper:~$ 

```

---

### Post by PriceChild on 2006-10-26
> **dbott67 said:**
> Others have reported problems opening Synaptic from the menu.  The workaround (at present) is to open a terminal and type:
```
sudo synaptic
```-DavePlease use gksudo when launching graphical apps: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by cabber on 2006-10-26
> **dbott67 said:**
> Others have reported problems opening Synaptic from the menu.  The workaround (at present) is to open a terminal and type:
```
sudo synaptic
```
-Dave

This is what I get:

```
chop@chop-dapper:~$ sudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
chop@chop-dapper:~$
```

---

### Post by dbott67 on 2006-10-26
Thanks... 

I read aysui's article last week about gksudo vs. sudo and forgot all about it.

Repeat after me: gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo, gksudo.

There.  I shant forget now! :)

---

### Post by PriceChild on 2006-10-26
Ok in the first post you said Dapper 6.10.... dapper is 6.06, edgy is 6.10. Please clarify.

[U]EDIT
[U]
check this:[/U][/U] ```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```ripped from: [http://www.ubuntuforums.org/showthread.php?t=261838](http://www.ubuntuforums.org/showthread.php?t=261838)[]("http://ubuntuforums.org/showthread.php?t=239238")

---

### Post by cabber on 2006-10-26
> **PriceChild said:**
> Ok in the first post you said Dapper 6.10.... dapper is 6.06, edgy is 6.10. Please clarify.

[U]EDIT
[U]
check this:[/U][/U] ```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```ripped from: [http://www.ubuntuforums.org/showthread.php?t=261838](http://www.ubuntuforums.org/showthread.php?t=261838)[]("http://ubuntuforums.org/showthread.php?t=239238")

Sorry about that, Using 6.06 Dapper.

---

### Post by cabber on 2006-10-26
> **PriceChild said:**
> Ok in the first post you said Dapper 6.10.... dapper is 6.06, edgy is 6.10. Please clarify.

[U]EDIT
[U]
check this:[/U][/U] ```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```ripped from: [http://www.ubuntuforums.org/showthread.php?t=261838](http://www.ubuntuforums.org/showthread.php?t=261838)[]("http://ubuntuforums.org/showthread.php?t=239238")

```
chop@chop-dapper:~$ sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
ln: creating symbolic link `/usr/lib/libvte.so.4' to `/usr/lib/libvte.so.9': File exists
chop@chop-dapper:~$
```

Not sure what this is

---

### Post by cabber on 2006-10-26
Nevermind.  That did the trick.  Thank you for your assistance. I do appreciate it.

Cabber

---

