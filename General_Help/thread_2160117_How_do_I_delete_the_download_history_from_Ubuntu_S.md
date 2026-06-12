---
title: "How do I delete the download history from Ubuntu Software Center on Ubuntu 12.10?"
date: 2013-07-05
forum: General Help
---

### Post by thedoctor7 on 2013-07-05
I'm using Ubuntu 12.10 and need to delete the download history from the Ubuntu Software Center for privacy reasons. I've already tried "Forget activities" in Privacy (from the System Settings), but it doesn't delete the download history. I've tried running the following command, but it didn't work either:

```
sudo rm -rf /var/log/apt/history.log /var/log/dpkg.log
```

 Then I went into /var/log and removed all the files that looked like history.log and dpkg.log, but still nothing.

Any ideas would be greatly appreciated.

---

### Post by kc1di on 2013-07-05
Hi,
Got to a terminal and type the following commands see if it works:
```
sudo apt-get clean 
sudo apt-get autoclean
```

Also you may want to install ubuntu tweak found [here]("http://ubuntu-tweak.com/") and run the janitor.

---

### Post by Irihapeti on 2013-07-05
Please use the default font and put code snippets between ```

``` tags. It makes it easier to read.

---

