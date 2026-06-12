---
title: "Problem Installing HPLIP"
date: 2007-02-26
forum: General Help
---

### Post by ngrundy on 2007-02-26
Hello, 

I downloaded the HPLIP file from the HPLIP website to run my HP deskjet F335 all in on printer. I follow the first step and type "sh ./hplip-1.7.1.run" at the terminal prompt and I get the following error. 
"no such file or directory" 

Can anyone tell me what I did wrong or where I should put the file in order to run it. I had it in my "Home" directory, should it be somewhere else?

Ubuntu 5.10 

Thanks in advance

---

### Post by taurus on 2007-02-26
I guess you are not in the right directory when you ran that command.  It's probably in ~/Desktop so do

```
cd ~/Desktop
chmod 755 hplip-1.7.1.run
sudo ./hplip-1.7.1.run
```

---

