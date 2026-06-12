---
title: "problem installing Interactive C"
date: 2008-02-13
forum: General Help
---

### Post by freakinjonathan on 2008-02-13
Hello im running Ubuntu 7.10 (gutsy)
specifically this file
[http://www.botball.org/educational-resources/ic.php](http://www.botball.org/educational-resources/ic.php)
it's for a robotics competition :)
ok i downloaded and extracted the file and when i went to it in the terminal and i ran 
./icgui 
it tells you that it can't find the libraries or somthing like that any help would be appreciated. maybe im using the wrong command??

---

### Post by xeth_delta on 2008-02-13
Welcome to the forums!
That means that there are some libraries missing, and that you would need to install them. Could you please be more specific on the errors? Please post the message on the thread between code tags.

Also, did you check if there is an install script for the program you are trying to run?

---

### Post by freakinjonathan on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [http://www.botball.org/educational-resources/ic.php](http://www.botball.org/educational-resources/ic.php) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				alright i was fiddling with the darn thing again. I got more information The library was called 

"libstdc++.so.5" 
im not sure how to install a singe library like that.:(

---

### Post by xeth_delta on 2008-02-15
> **freakinjonathan said:**
> **This post could be related to an Ubuntu bug filed at**: [http://www.botball.org/educational-resources/ic.php](http://www.botball.org/educational-resources/ic.php) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				alright i was fiddling with the darn thing again. I got more information The library was called 

"libstdc++.so.5" 
im not sure how to install a singe library like that.:(

The library is found in the repositories. You can install it with one of the graphical interfaces to the package management system (synaptic/adept) or from the command line:

```
sudo apt-get install libstdc++5
```

---

