---
title: "Searching with Recoll; how to use different directories"
date: 2019-06-08
forum: General Help
---

### Post by mysticmuse2 on 2019-06-08
I'm having trouble getting beyond simple search with Recoll, the docs for which are here:  [https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html](https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html)

I installed it OK, created a database that uses a few different directors but I can't understand how to narrow the search to particular directory as the means for doing this seem quite complicated and detailed and I can't find a usable example or a step by step procedure.     The docs are very though but full of technical terms and concepts that are not understandable by the average user.  

So what are the steps for narrowing a search to a particular directory within the group of directories that you have indexed?  There appears to be no simple option for this and instead you have to do some tech preparation that I can't follow.

---

### Post by TheFu on 2019-06-08
Are you using the GUI interface or the CLI version?  I cannot help with the GUI.

---

### Post by dragonfly41 on 2019-06-08
As an alternative try [ripgrep]("https://github.com/BurntSushi/ripgrep")
navigate to your target directory
run a command such as

rg -i <searchPattern>

---

### Post by mysticmuse2 on 2019-06-08
Yes, the GUI version

---

