---
title: "unable to get rid of Tor browser"
date: 2016-09-10
forum: General Help
---

### Post by s9032g@comcast.net on 2016-09-10
I have tried several ideas for completely getting rid of the Tor browser; however it remains accessible even though terminal tells me that it isn't installed. What should I do?

---

### Post by oldos2er on 2016-09-10
How did you install it?

---

### Post by s9032g@comcast.net on 2016-09-11
i tried a few things before it worked. Probably went right back to the root of it. Now it is installed so well that it won't go away.

---

### Post by s9032g@comcast.net on 2016-09-11
I just looked back and see that I installed ppa.launchpad.net/webupd8stream/tor-browser/ubuntu xenial main   also same with source code. This appears in "other software".  I have now unchecked it but probably need to uninstall it??? How?

---

### Post by s9032g@comcast.net on 2016-09-11
OK I guess I found the answer 

 sudo apt-get remove tor-browser
rm -r ~/.tor-browser-en

I don't see Tor anymore. Am I ok?

---

### Post by oldos2er on 2016-09-11
I'd say so. Would you please mark the thread 'Solved'? Thanks.

---

### Post by s9032g@comcast.net on 2016-09-11
I also launched nautilus as root and was able to delete a Tor file under etc

---

