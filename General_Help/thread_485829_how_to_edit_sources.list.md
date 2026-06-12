---
title: "how to edit sources.list?"
date: 2007-06-27
forum: General Help
---

### Post by nate22 on 2007-06-27
ok so aparently theres something wrong w/ my sources.list file

it keeps saying.

.E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 26 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


so i typed in 
sudo vim /etc/apt/sources.list
a message saying 

that i need to swap some file blah blah blah

is there any way i can edit this sources.list?

because of it i cant do (add/remove, any of the apt commands or put new stuff in comp )

---

### Post by Nate53085 on 2007-06-27
Could you please give us the exact error message

---

### Post by strabes on 2007-06-27
```
sudo nano /etc/apt/sources.list
```

Delete the offending line, ctrl+o to save, ctrl+x to exit.

---

### Post by nate22 on 2007-06-27
omg strabes.. im officialy in love w/u 

ur a life saver man 

now i gota figure out how to install wine..

---

### Post by speaker219 on 2007-06-27
For the noobs, it would be easier to use:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by speaker219 on 2007-06-27
> **nate22 said:**
> 
now i gota figure out how to install wine..
```
sudo apt-get install wine
```
done.

---

### Post by Qu4k3R on 2007-06-28
I am using this:

> 
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main


for wine.

See how to install the gpg key here:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

PS:
Gedit (or Kate) might be easier to use than nano or vim

---

