---
title: "Libre Office"
date: 2014-02-07
forum: General Help
---

### Post by punkboy22 on 2014-02-07
is there a way to uninstall libre office all together and then re-install it or just repair it? apparently mine flaked on me as i was installing 13.10 on my hp mini 110

---

### Post by Lars Noodén on 2014-02-07
You could try purging and installing again:

```

sudo apt-get purge libreoffice
sudo apt-get update
sudo apt-get install libreoffice

```

Or you could try reinstalling:

```

sudo apt-get --reinstall install libreoffice

```

What are the symptoms that show that something is amiss?

---

### Post by Bashing-om on 2014-02-07
punkboy22; Hi ! again >

Might try:
```

sudo dpkg-reconfigure libreoffice

```
as a 1st approximation, see what the package manager relates to "fix" the package. -pay attention to the "components" -
As to (re-)installing:
```

sudo apt-get install --reinstall libreoffice

``` see how that goes.

Else: as a last resort ->
 One can completely remove it ( ohhh not a good thing, as libre office is deeply entwined in the operating system); no telling what all will also be removed ! Pay real close attention and note what all is going to be removed. If these exterior components are not re-installed, will likely break your system.
AND then:
Install libre office once more- noting again from the above what was removed, and what now will not be (re-)installed. Re- install them.
As you may well imagine, could be a painful process.
Always -> maintain good backups, one can never tell when a (RE-)install operation will be called forth ! -Power failure never happens at the best of times -

[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by punkboy22 on 2014-02-08
thanks for the help i will try this and yeah found out the hard way that libre office is super entwined with the OS bad idea to purge it lol

---

