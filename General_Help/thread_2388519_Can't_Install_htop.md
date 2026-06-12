---
title: "Can't Install htop"
date: 2018-04-04
forum: General Help
---

### Post by dannyk2 on 2018-04-04
Have been trying and failing to install "htop" from the command line using:

```

       sudo apt-get install htop

                  and

      sudo apt install htop

```

Could someone help please. I am running Ubuntu GNOME 17.10

Thanks

---

### Post by QIII on 2018-04-04
Hello!

Would you please post the results of those commands?

---

### Post by HermanAB on 2018-04-04
Hmm, try something like:
$ dpkg-query -S 'htop'

to find out exactly which package htop belongs to.

---

### Post by sudodus on 2018-04-04
What version and flavour of Ubuntu are you running?

---

### Post by dannyk2 on 2018-04-04
I am running Ubuntu GNOME 17.10 and when i have tried to install "htop" from the command line using:

```

dannyk2@dannyk2:~$ sudo apt-get install htop
[sudo] password for dannyk2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package htop
dannyk2@dannyk2:~$

```

I get exactly the same output as above when using:

```

sudo apt install htop

```

---

### Post by deadflowr on 2018-04-04
It's in the universe repository. (also known as the community repository)
So make sure universe is enabled in the software sources.
I would double check that the repositories settings are proper with a quick
```
sudo apt update
```

post back the results if anything seems iffy.

---

### Post by sudodus on 2018-04-05
```

sudo add-apt-repository universe
sudo apt update
sudo apt install htop

```

should work in Ubuntu Gnome 17.10.

If not, please post the output of all those command lines.

---

