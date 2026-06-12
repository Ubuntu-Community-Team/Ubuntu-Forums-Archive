---
title: "How do i restore gcc back to original?"
date: 2007-03-04
forum: General Help
---

### Post by dwf_starband on 2007-03-04
Being new to ubuntu and linux i have been playing around trying everything out.  In the Synaptic Package Manager i somehow managed to install and delete different versions of gcc.

Now some programs arent working including Synaptic.  I cant use apt-get because i get an error 

apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Is there an easy way to restore gcc back to the way it was?  I would rather not do a complete new installation of ubuntu because ive got stuff on here now that i use.

Thanks for your help.

dennis

---

### Post by PriceChild on 2007-03-04
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
sudo apt-get dist-upgrade
```Should get everything for you.

---

### Post by navneeth on 2007-03-04
Isn't it better to use 'aptitude' over 'apt-get'?

---

### Post by PriceChild on 2007-03-04
> **navneeth said:**
> Isn't it better to use 'aptitude' over 'apt-get'?I suppose :) However if you use apt-get half the time and aptitude the other half then you will not get the benefits as aptitude attempts to maintain its own history.

I'm just used to apt-get from too much ubuntu+1'ing :)

---

### Post by dwf_starband on 2007-03-04
As i posted in my original question i cannot use apt-get because of the error i quoted.

I also tried aptitude and get the same error.

which is,

aptitude: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


any help on my specific problem?

I apreciate any help you can give me.

dennis

---

