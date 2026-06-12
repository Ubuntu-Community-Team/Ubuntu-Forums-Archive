---
title: "In great detail, explain to me how to get java?"
date: 2006-10-15
forum: General Help
---

### Post by DiscoSamurai on 2006-10-15
I just need java and I'm not all that linux savvy, so please help me as best as possible?

---

### Post by Anonii on 2006-10-15
Lets see:

```
wget  http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-bin_1.5.0-06-1_i386.deb
```

```
wget http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-jre_1.5.0-06-1_all.deb
```

```
sudo aptitude install unixodbc
``` 


```
sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb
```

Here, accept the licence, and the installer will fail, but you dont care.

```
sudo dpkg -i sun-java5-bin_1.5.0-06-1_i386.deb
```

It will say that it failed, too, but you still dont care.

```
sudo dpkg --configure -a
```

To fix them.

And now:

```
sudo update-java-alternatives -s java-1.5.0-sun
```
and if that doesnt work, do this:
```
update-java-alternatives -l
```
if to works, dont mess with the latter.

That did it to me, both in Edgy and in Dapper.

Good luck!

(Source: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) )

---

### Post by NeoLithium on 2006-10-15
I think the easiest way to get java, is to install automatix.

```

**In a terminal window**
sudo gedit /etc/apt/sources.list 

**In the editor window, at the bottom of the page, add this:**

deb http://www.getautomatix.com/apt dapper main

**Save the file, and exit. Then type each of the following lines individually in the terminal window:**

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

sudo apt-get update
sudo apt-get install automatix2


```

Once you're done, automatix2 can be started by typing ```
 sudo automatix2
``` or using the icon (I'm not sure where it appears in GNOME)  Then it's just a simple matter of select the packages you want, and click apply.  Voila, easy!

---

### Post by chalex on 2006-10-15
There's a page about it here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by jpkotta on 2006-10-15
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

