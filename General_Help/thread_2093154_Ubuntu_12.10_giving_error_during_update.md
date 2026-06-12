---
title: "Ubuntu 12.10 giving error during update"
date: 2012-12-10
forum: General Help
---

### Post by 5prasad on 2012-12-10
Hello Everyone,

I am using quantal quetzal but suddenly since 3-4 days. I am not able to update.

W:Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

This is error I am facing. Please help .

Thanks in advance.

---

### Post by Bucky Ball on 2012-12-10
This repository may be down. Try unticking it in your Software Sources and try again.

---

### Post by ibjsb4 on 2012-12-10
If Im looking at the right package, there's no build for 12.10.

[https://launchpad.net/~fyrmir/+archive/compiz-plugins](https://launchpad.net/~fyrmir/+archive/compiz-plugins)

---

### Post by 5prasad on 2012-12-10
I tried unticking it didn't work.

@ibjsb4  You are right. There is no package available.

---

### Post by ibjsb4 on 2012-12-10
> **5prasad said:**
> I tried unticking it didn't work.

Do you mean that you cannot uncheck it?

---

### Post by 5prasad on 2012-12-11
There is no such repository to untick ..

---

### Post by NightsShadeQueen on 2012-12-11
Can you find them in /etc/apt/sources.list or /etc/apt/sources.list.d ?

---

### Post by Bucky Ball on 2012-12-11
First you say unticking makes no difference then you say they're not there to untick ... 

You can't find any repostitories with a name containing:

 [http://ppa.launchpad.net/fyrmir/comp]("http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/source/Sources")

???

They must be there or you wouldn't be getting the error you posted. Sure you're looking in the right place? Open update manager and at the bottom left corner you should see 'Settings'. Click that, then the 'Other Software' tab. They are there somewhere.

When you find them, untick. You seem to be attempting to access the repos for 32bit _*and*_ 64bit. That might be another part of your problem ...

---

### Post by vasa1 on 2012-12-11
> **Bucky Ball said:**
> ... You seem to be attempting to access the repos for 32bit _*and*_ 64bit. ...
I was wondering about that as well. Not only 32-bit and 64-bit but also **source**. While having all three may not be part of the problem, I suspect there's some redundancy there.

---

