---
title: "Software update continues &quot;precise&quot; url status"
date: 2017-02-01
forum: General Help
---

### Post by John_Carver on 2017-02-01
Somewhere in my system is the following source:
[http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1) 
I understand why it's there but can't remove it.
Tried rm -rf /var/lib/apt/lists/* and removed entries on /etc/apt/secure.list to no avail
How do I remove this from "Software Updates"?

Thanks

---

### Post by Bucky Ball on 2017-02-01
Try in 

```
sudo nano /etc/apt/sources.list
```

Find the repo. Remove it or put a hash (#) next to it so it will be ignored.

---

### Post by John_Carver on 2017-02-01
So simple when you have the answer.
My good friend has told me that if you don't write it down its like it never happened
Will write this up
Thanks
Where do I find the "solved" button?

---

### Post by Bucky Ball on 2017-02-01
> **John_Carver said:**
> 
Where do I find the "solved" button?

Looks like you found it. :)

I use a lightweight app called Zim for keeping all the handy hints. You'll find it in the Software Centre or whatever package manager you are using to install software (or install using a terminal). 

I personally do:

```
sudo apt autoremove
sudo apt update
sudo apt dist-upgrade
```

... once or twice a week in a terminal and don't use the GUI at all. 

Enjoy. :)

---

### Post by John_Carver on 2017-02-01
I was covering Ubuntu 16.10 32 bit and your solution worked
I also run Ubuntu 16.10 64 bit on a lap top and this fix didn't work..strange
Thoughts?
Have been doing the terminal commands since having the problem
I'm using Workflowy
[https://workflowy.com/](https://workflowy.com/)

---

