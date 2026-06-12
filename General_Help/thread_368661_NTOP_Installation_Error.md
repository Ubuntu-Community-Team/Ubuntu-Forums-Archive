---
title: "NTOP Installation Error"
date: 2007-02-23
forum: General Help
---

### Post by donkeyspunk on 2007-02-23
Hi:

I am trying to install NTOP on Ubuntu 6.10 and during the ./configure part of NTOP, I am getting this error:

configure: error: Unable to find RRD: please use --with-rrd-home=DIR

Seems to be a Round Robin Database that I can't find. 

Does anyone know the apt-get command to install this or know where I can find the source?


Thanks

-D

---

### Post by Strider on 2007-02-23
Are you compiling from source?  Why not use the one available in the repository?  It's available in the universe repo.  If you want to compile you probably need to install the "rrdtool" package, which is also in the universe repo. 

Go with the ntop package unless you need to recompile for a specific reason.

-Mike

---

### Post by donkeyspunk on 2007-02-23
I've tried sudo apt-get install ntop but it always comes back "package name not found"

---

### Post by Strider on 2007-02-23
It's in the Universe repository so you need to edit /etc/apt/sources.list file and uncomment the line for the "universe" repo.  Then do the following:

apt-get update #This will update the package available
apt-cache search ^ntop # this will run a query against the updated package list on your computer to verify ntop is available.  If it is you should see a listing for it

Then run "apt-get install ntop" and it should work.

Check out this link: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) - it's the ubuntu guide.  Look at the top for adding additional repositories.

-Mike

---

### Post by donkeyspunk on 2007-02-26
that worked.....thanks.....

---

### Post by garret on 2008-07-21
Ehh, yeah, but what if you WANT to install by source. What's the answer to the problem as stated?

---

