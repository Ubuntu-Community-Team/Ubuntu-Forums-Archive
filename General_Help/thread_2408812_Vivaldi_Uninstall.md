---
title: "Vivaldi Uninstall?"
date: 2018-12-23
forum: General Help
---

### Post by Daveski17 on 2018-12-23
Hello,

I'm thinking about downloading the latest version of Vivaldi. I ran it about four years ago on Ubuntu on my old laptop. I just want to check what the sudo command would be to uninstall it in case of any problems:

sudo apt-get purge-vivaldi-stable 

sudo apt purge vivaldi

I'm guessing it's something like one of these. Does anyone know the exact syntax, thanks.

---

### Post by deadflowr on 2018-12-23
```
sudo apt purge vivaldi
```
would be closer.
```
sudo apt-get purge-vivaldi-stable 
```
would bring up an error saying no such apt-get command found, since there is no such apt-gt command for purge-vivaldi-stable since no such apt-get command exists as written.
You can always run a quick dpkg --list to see what the true package name is like
```
dpkg -l | grep vivaldi
```
in case is does have anything extra like stable tagged on it.
Then you can run that first command fine.

---

### Post by howefield on 2018-12-23
Here is the help page from the vivaldi website :[https://help.vivaldi.com/article/how-to-uninstall-vivaldi/](https://help.vivaldi.com/article/how-to-uninstall-vivaldi/)

I'd use apt to install the package and apt to remove it.

```
sudo apt purge vivaldi-stable
```

Unless you really are using Ubuntu 14.04 in which case I think you'd have to use apt-get as opposed to apt in the command.

---

### Post by Daveski17 on 2018-12-23
> **deadflowr said:**
> ```
sudo apt purge vivaldi
```
would be closer.
```
sudo apt-get purge-vivaldi-stable 
```
would bring up an error saying no such apt-get command found, since there is no such apt-gt command for purge-vivaldi-stable since no such apt-get command exists as written.
You can always run a quick dpkg --list to see what the true package name is like
```
dpkg -l | grep vivaldi
```
in case is does have anything extra like stable tagged on it.
Then you can run that first command fine.

OK thanks.

---

### Post by Daveski17 on 2018-12-23
> **howefield said:**
> Here is the help page from the vivaldi website :[https://help.vivaldi.com/article/how-to-uninstall-vivaldi/](https://help.vivaldi.com/article/how-to-uninstall-vivaldi/)

I'd use apt to install the package and apt to remove it.

```
sudo apt purge vivaldi-stable
```

Unless you really are using Ubuntu 14.04 in which case I think you'd have to use apt-get as opposed to apt in the command.

OK thanks. I really am using the LTS version of 14.0.4 at the moment. I'll upgrade just before April 30, 2019 I think.

---

### Post by deadflowr on 2018-12-23
> Unless you really are using Ubuntu 14.04 in which case I think you'd have to use apt-get as opposed to apt in the command.
fwiw you can use apt on 14.04, just not autoremove and a couple other options, but install remove and purge are all available on apt for 14.04.

---

