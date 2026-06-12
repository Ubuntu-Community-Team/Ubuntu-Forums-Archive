---
title: "How can I view package list in terminal?"
date: 2008-05-06
forum: General Help
---

### Post by Graeme2804 on 2008-05-06
I would like to be able to see what packages are installed and what need to be installed etc. etc. in terminal/PuTTY.

Is there a way of doing this?  No GUI please, not using a desktop for the machine I need it on so can't see the screen.

---

### Post by utUtu on 2008-05-06
> **Graeme2804 said:**
> I would like to be able to see what packages are installed and what need to be installed etc. etc. in terminal/PuTTY.

Is there a way of doing this?  No GUI please, not using a desktop for the machine I need it on so can't see the screen.

You can use apt-get or aptitude or dpkg.

---

### Post by Monicker on 2008-05-06
This will show you what is installed
```

dpkg --get-selecctions
```


I'm not sure what you mean by "needs to be installed".

If you want to check what dependencies will be installed for a package without actually installing it, do this:

```
sudo apt-get -s install packagename
```

---

### Post by Graeme2804 on 2008-05-06
> **Monicker said:**
> This will show you what is installed
```

dpkg --get-selecctions
```


I'm not sure what you mean by "needs to be installed".

If you want to check what dependencies will be installed for a package without actually installing it, do this:

```
sudo apt-get -s install packagename
```

Hi,

I meant what can be installed, like in synaptic you see everything that you can install, but i need it in terminal.

dpkg --get-selections  shows what i have installed which will do fine thankyou.

Once again, problem solved by UbuntuForums :)

---

### Post by oldos2er on 2008-05-06
> **Graeme2804 said:**
> I would like to be able to see what packages are installed and what need to be installed etc. etc. in terminal/PuTTY.

Is there a way of doing this?  No GUI please, not using a desktop for the machine I need it on so can't see the screen.

 Use the command "aptitude"

---

### Post by Monicker on 2008-05-06
/var/lib/dpkg/available should contain a listing of all available packages.

---

