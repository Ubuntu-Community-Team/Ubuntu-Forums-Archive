---
title: "[SOLVED] &amp;quot;  bin file &amp;quot;"
date: 2008-06-09
forum: General Help
---

### Post by Dyffo on 2008-06-09
[SIZE="3"]Want to  run Google Earth on UBUNTU - downloaded a bin file - any ideas on how to open and save[/SIZE]:confused:

---

### Post by Vivaldi Gloria on 2008-06-09
> **Dyffo said:**
> [SIZE="3"]Want to  run Google Earth on UBUNTU - downloaded a bin file - any ideas on how to open and save[/SIZE]:confused:

Do not install GE like that. First goto 

[http://www.medibuntu.org/](http://www.medibuntu.org/)

and read around. Then add medibuntu to your repository list by

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

These lines are for Ubuntu 8.04 btw.

Then open synaptic from you sytem menu. Click Refresh. Search for GE. Then select it and install.

---

### Post by rampageoberon on 2008-06-09
Have a look at the medibuntu page/repositories. I'm sure they have packages for google earth that you can install using synaptic

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by DJ_Peng on 2008-06-09
With apologies to Vivaldi Gloria, there are times when you don't want to install a program from the repos so you can use the latest version available, not the latest version to hit the repos. Google Earth may be one of those programs for some people, although it wasn't for me. Luckily Tombuntu has a [tutorial for installing GE in Ubuntu]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/"). It's easy, it's safe, and when Google releases a new version with new features you won't have to wait for the repos to get it before you can play with the new goodies. (This is definitely an issue for some programs, like Firefox. I'm not sure how much lag there is for GE between release and the update reaching Medibuntu.)

---

### Post by Vivaldi Gloria on 2008-06-09
> **DJ_Peng said:**
> With apologies to Vivaldi Gloria, there are times when you don't want to install a program from the repos so you can use the latest version available, not the latest version to hit the repos. Google Earth may be one of those programs for some people, although it wasn't for me. Luckily Tombuntu has a [tutorial for installing GE in Ubuntu]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/"). It's easy, it's safe, and when Google releases a new version with new features you won't have to wait for the repos to get it before you can play with the new goodies. (This is definitely an issue for some programs, like Firefox. I'm not sure how much lag there is for GE between release and the update reaching Medibuntu.)

In general we should direct the new users to the preferred method which is to use repos.

---

