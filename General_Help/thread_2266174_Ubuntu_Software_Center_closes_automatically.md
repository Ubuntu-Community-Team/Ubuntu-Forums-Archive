---
title: "Ubuntu Software Center closes automatically"
date: 2015-02-20
forum: General Help
---

### Post by Mehul_Chirania on 2015-02-20
I'm running 14.04 LTS and everytime I open the software center it closes automatically. New to Ubuntu so need help. I tried the following codes hoping to get some o/p but got nothing.
sudo apt-get update && sudo apt-get upgrade
I get nothing. Somebody help me please?  :?

---

### Post by v3.xx on 2015-02-20
What happens if you open it in terminal?
```
gksudo software-center
```
Get any errors?

Edit
Also try
```
software-center
```

---

### Post by ian-weisser on 2015-02-20
> **Mehul_Chirania said:**
> sudo apt-get update && sudo apt-get upgrade
I get nothing.

Really nothing? The terminal goes down one line, returns to a prompt, and there is *no output at all*?
Or is there a bunch of output that results in no change to your system?

---

