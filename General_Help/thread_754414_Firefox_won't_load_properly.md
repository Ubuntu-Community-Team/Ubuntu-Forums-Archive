---
title: "Firefox won't load properly"
date: 2008-04-13
forum: General Help
---

### Post by thenetduck on 2008-04-13
Hi I have been having problems getting my firefox to load properly I installed it with the repo and it would work. Right now the only way I can get it to run is to do this: /usr/bin/firefox/./firefox

I want to be able to just run "firefox" in my terminal and have it run firefox for me. Does anyone know how I can do this? 

Thanks 

The Net Duck

---

### Post by rocky5051 on 2008-04-13
First, update your repositories.

```
sudo apt-get update
```

Then reinstall Firefox.

```
sudo apt-get remove firefox
sudo apt-get purge firefox
sudo apt-get install firefox
```

Purging it will make sure you get the most recent version and make sure it's clean and not corrupted in any way.

---

### Post by thenetduck on 2008-04-13
> **rocky5051 said:**
> First, update your repositories.

```
sudo apt-get update
```

Then reinstall Firefox.

```
sudo apt-get remove firefox
sudo apt-get purge firefox
sudo apt-get install firefox
```

Purging it will make sure you get the most recent version and make sure it's clean and not corrupted in any way.

Thanks for the help, but that didn't work.....

Any other suggestions? Thanks once agian

The Net Duck

---

