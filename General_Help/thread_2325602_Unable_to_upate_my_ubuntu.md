---
title: "Unable to upate my ubuntu"
date: 2016-05-23
forum: General Help
---

### Post by alfirdaous on 2016-05-23
Hello everybody,

I am trying to update my ubuntu, but I cannot do it:

Error:
```

Fetched 3,365 kB in 10s (322 kB/s)                                                                                               
W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/binary-amd64/Packages  Hash Sum mismatch


W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/binary-i386/Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.

```


Info
```

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

Thanks in advance

---

### Post by mörgæs on 2016-05-24
Which *sarge* are you referring to in the URL? Is it Debian Sarge?

---

### Post by alfirdaous on 2016-05-24
> **mörgæs said:**
> Which *sarge* are you referring to in the URL? Is it Debian Sarge?

Debian Sarge

---

### Post by mörgæs on 2016-05-24
That doesn't sound good to me. Debian Sarge is an old system which lost support many years ago. 

Though Ubuntu 12.04 is still supported the number of active users is decreasing. 

Have you thought of a beginning from a fresh install of 16.04?

---

### Post by alfirdaous on 2016-05-24
So to solve this problem I should move to 16.04?

---

### Post by howefield on 2016-05-24
> **alfirdaous said:**
> So to solve this problem I should move to 16.04?

No, not to solve this problem, but for other reasons possibly.

Remove the offending third party repositories is all you need to do to solve your problem.  

Is this a server ?

---

### Post by RobGoss on 2016-05-24
```
 
W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/binary-amd64/Packages Hash Sum mismatch


W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/contrib/binary-i386/Packages Hash Sum mismatch
```


What Howefield is trying to say is remove the following third-party repositories in order to correct your problem 

Go to **Software Update** click on** Other Software** you will see a list of third-party repositories choose the ones you listed and highlight them to just remove them

Close and let the list reload and exit

---

### Post by alfirdaous on 2016-05-24
This is a server, how can I remove it using a command line?

---

### Post by yetimon_64 on 2016-05-24
> **alfirdaous said:**
> This is a server, how can I remove it using a command line?

By using the command ...
```
sudo nano /etc/apt/sources.list
```

In the editor either delete the two lines noted above OR put a # symbol at the start of each of the two to comment them out (stops them being used).

Save the file by pressing the key combination "Ctrl + O", then press the Enter key to actually write the file.

Pressing the key combination "Ctrl + X" will exit the editor (nano).

Edit. Once you have exited the nano editor then try the update process again "sudo apt-get update" etc as you normally would.

---

### Post by howefield on 2016-05-25
> **alfirdaous said:**
> This is a server, how can I remove it using a command line?

Yetimon_64's advice should fix it, you might also be interested in this thread..

[https://sourceforge.net/p/webadmin/bugs/4742/](https://sourceforge.net/p/webadmin/bugs/4742/)

---

### Post by alfirdaous on 2016-05-25
I added these 2 lines to download the webmin a long time ago

---

### Post by mörgæs on 2016-05-29
Yes, and now they are obsolete. Here is a [new approach]("http://www.unixmen.com/install-webmin-ubuntu-14-04/").

---

