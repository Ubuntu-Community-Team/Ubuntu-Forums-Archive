---
title: "pip install errors - wrong software version?"
date: 2015-09-06
forum: General Help
---

### Post by Sky_Dog on 2015-09-06
Hi all,

I want to use python 2.7 in Ubuntu for my programs, but when I start the command `pip install eth-testrpc`, then I get some installation errors starting in the line 200: [http://paste.ubuntu.com/12297399/](http://paste.ubuntu.com/12297399/)

The pip version is (pip -V)
> pip 1.5.6 from /usr/lib/python2.7/dist-packages (python 2.7)

Any idea what do I have to do to run `pip install eth-testrpc` successfully? Do I have to install anything new? In the log there is some information about [COLOR=#000000]utils_py3.py. Is there a way to install the eth-testrpc package without using python 3?[/COLOR]

Regards
Skydog

---

### Post by monkeybrain20122 on 2015-09-06
I don't know, but seems like the package is in python3 so you may try the python3 version of pip

```
sudo apt-get install python3-pip

```
then 
 ```
sudo pip3 install packagename
```

But you may want to delete the partially installed junks first (if any)

---

### Post by Sky_Dog on 2015-09-06
> **monkeybrain20122 said:**
> I don't know, but seems like the package is in python3 so you may try the python3 version of pip

```
sudo apt-get install python3-pip

```
then 
 ```
sudo pip3 install packagename
```

But you may want to delete the partially installed junks first (if any)

Thanks a lot [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403")!

---

