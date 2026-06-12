---
title: "How to undo sudo chmod ugo+wx /"
date: 2013-12-23
forum: General Help
---

### Post by danny20 on 2013-12-23
I think i followed bad advice and did sudo chmod ugo+wx /
  this was supposed to give me write permissions to my secondary ext4  storage partition but i think i did it for the system partition? So did i just give myself write and execute permissions outside of home  as well? I bet that's terrible for security?
  Please let me know what I did, how to undo it, and how to do it for the data partition instead :)
  Thank you!

---

### Post by steeldriver on 2013-12-23
Hello and welcome to the forums

If you **didn't** add the -R (recursive) flag then you can undo the command simply by setting the permissions back to the default ones - either

```
sudo chmod u=rwx,go=rx /
```

or (in octal)

```
sudo chmod 755 /
```

If you **did** add the -R flag then it is pretty much not feasible to get everything back in order - there are too many subtly different permissions scattered around the place - and so a re-install is your best option.

---

### Post by danny20 on 2013-12-23
yes that works! Thank you!

How to make the data partition writeable? i tried to chown it to my user but still can't write :(

---

### Post by oldos2er on 2013-12-23
If the partition is only used for storage, use something like ```
sudo chown -R user:user /media/sdX
``` Replace "user" with your user name, and "/media/sdX" with wherever the partition is mounted.

---

### Post by danny20 on 2013-12-23
it worked but only after restart
thank you!

---

### Post by oldos2er on 2013-12-23
You're welcome. Please mark the thread as "Solved" (under Thread Tools at the top of the page).

---

