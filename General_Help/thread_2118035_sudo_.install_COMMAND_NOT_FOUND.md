---
title: "sudo ./install COMMAND NOT FOUND"
date: 2013-02-20
forum: General Help
---

### Post by vasava on 2013-02-20
I am trying to install Ansys 14 on my computer. It has Ubuntu 12.04 64-bit. 

The installation directory has file named INSTALL (its just a text file) which does not work with 'sudo ./INSTALL'. 

I also tried mounting iso file but it still does not work.

Any suggestions or idea?

Thanks!!

---

### Post by sudodus on 2013-02-20
> **vasava said:**
> I am trying to install Ansys 14 on my computer. It has Ubuntu 12.04 64-bit. 

The installation directory has file named INSTALL (its just a text file) which does not work with 'sudo ./INSTALL'. 

I also tried mounting iso file but it still does not work.

Any suggestions or idea?

Thanks!!
Welcome to the Ubuntu Forums :-)

1. Linux makes a difference between UPPER and lower case letters in file names, so it is important to get that right.

2. The problem might be that the file has not execution permission. The easy way would be to run

```
sudo sh INSTALL
```
or (if there are some bash-specific commands)
```
sudo bash INSTALL
```

The other alternative would be to check the permissions with
```
ls -l INSTALL
```
and change them with
```
sudo chmod ugo+x INSTALL
``` and then you should be able to run the file with
```
sudo ./INSTALL
```

---

### Post by vasava on 2013-02-20
sudo sh ./INSTALL workerd fine. 

Thank you [[COLOR=#000000]suodus[/COLOR]]("http://ubuntuforums.org/member.php?u=1499021") for your answer.

---

### Post by sudodus on 2013-02-20
You are welcome :-)

---

### Post by 3rdalbum on 2013-02-20
You could also do
sudo such
./install

---

### Post by sudodus on 2013-02-20
> **3rdalbum said:**
> You could also do
sudo such
./install
???

---

### Post by aarons6 on 2013-02-20
one other thing you should know, if you type ls and the INSTALL isnt green you need to chmod +x it.. 

that will make it executable so you can run it.

---

### Post by schragge on 2013-02-20
> **sudodus said:**
> ???I guess **3rdalbum** means *sudo su*, but I don't see the need for it here. If ./install installs somewhere outside your home directory, *sudo sh install* would be enough.

---

