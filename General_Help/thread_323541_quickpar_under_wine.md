---
title: "quickpar under wine"
date: 2006-12-22
forum: General Help
---

### Post by dragon76 on 2006-12-22
I successfully installed quickpar under wine.  When I try to create par files though I get a failed: source not found error.  Wondering if anyone else has experienced this and how they fixed it as I have seen multiple posts of people using it without problems.

Thanks

---

### Post by dragon76 on 2006-12-27
ttt, bump

---

### Post by BertP on 2007-12-17
> **dragon76 said:**
> I successfully installed quickpar under wine.  When I try to create par files though I get a failed: source not found error.  Wondering if anyone else has experienced this and how they fixed it as I have seen multiple posts of people using it without problems.

Thanks

I know this is an old post,  so just in case you're still out there...     ;)

I haven't tried to create par files but I did try to use quickpar to repair and  couldn't get it to work, however,  I did  find out how to automatically invoke the command line par2repair with nautilus! 

all you have to do is associate par2 extensions with custom command-line :

"xterm -hold -e par2repair"  and it works like a charm!

I found this tip here --> " Usenet binaries with Linux tutorial " [http://linux-is-sexy.blogspot.com/2005/12/usenet-binaries-with-linux-tutorial.html](http://linux-is-sexy.blogspot.com/2005/12/usenet-binaries-with-linux-tutorial.html)

...

back to your question, as for as I know, your only option for creating par files is using the command line program par2create

---

