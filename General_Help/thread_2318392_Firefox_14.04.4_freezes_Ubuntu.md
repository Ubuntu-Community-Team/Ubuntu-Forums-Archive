---
title: "Firefox 14.04.4 freezes Ubuntu"
date: 2016-03-25
forum: General Help
---

### Post by rosswmcgee on 2016-03-25
The last several days Firefox freezes Ubuntu and I have to shut down. I cleared the cache etc. still happening. Anyone else have the problem? 

Firefox 45.0 in synaptic.

---

### Post by ajgreeny on 2016-03-25
No, all good here with the same FF45 on Xubuntu-14.04-64bit system.

See what happens if you shutdown FF, rename the hidden .mozilla folder in your home with command ```
mv .mozilla .mozilla-bak
``` and then start FF again.  A problem in the FF profile can often cause this problem; a new profile then overcomes it.

---

### Post by rosswmcgee on 2016-03-25
No such file or directory

---

### Post by vasa1 on 2016-03-25
> **rosswmcgee said:**
> No such file or directory
Huh?

Try *mv ~/.mozilla* ...

---

### Post by ajgreeny on 2016-03-26
> **rosswmcgee said:**
> No such file or directory
I think there must be such a folder if you have used firefox.
Did you use the . at the start of the folder name, ie, **.mozilla**?

---

### Post by rosswmcgee on 2016-03-26
I went to synaptic,used the completely remove option. Re-installed firefox, and have not had a problem since. So we shall see. Thanks for your help.

---

### Post by vasa1 on 2016-03-27
Using Synaptic's "completely remove" is the same as running *sudo apt-get purge package_name_here*, I think. It won't remove *~/.mozilla*. If you have a messed up profile, your newly installed Firefox will use that same profile.

---

### Post by rosswmcgee on 2016-03-27
The proof will be in the pudding I guess. So far so good. I was freezing quite often but have yet to freeze since the Purge. 

I do have  folders  .mozlila also.mozilla-bak in my home directory when looking for hidden files. But terminal did not show them with above command. Now I hesitate 

to do anything and will leave well enough alone.  

Thanks

---

