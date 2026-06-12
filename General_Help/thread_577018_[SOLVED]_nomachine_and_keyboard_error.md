---
title: "[SOLVED] nomachine and keyboard error"
date: 2007-10-15
forum: General Help
---

### Post by milosz.galazka on 2007-10-15
Hello,

I just downloaded and installed nomachine. But I am experiencing one problem because if run nxclient and log into my home computer then keyboard in my NX session is not working (only ALT and CTRL are working). So if I try to type something on keyboard then nothing happens. 

Also I am curious if can watch movies, videoclips using nxclient? I enabled multimedia support but when I open something using smplayer (mplayer frontend) then it does not play anything.

Thanks

EDIT:
There was problem with libraries. After reboot everything is working fine.

---

### Post by sricketts on 2008-04-24
> **milosz.galazka said:**
> 
There was problem with libraries. After reboot everything is working fine.

Which libraries? What did you reboot -- the client or server? I am having a similar problem; I only get keyboard response for the number pad. I have rebooted the client (Ubuntu 7.10 32 bit), but do not have permissions to reboot the server. I have also tried the client on Ubuntu 7.04 (32 and 64 bit).

There is a similar bug report here: [http://www.nomachine.com/tr/view.php?id=TR11C01164](http://www.nomachine.com/tr/view.php?id=TR11C01164)

but the report says the problem is fixed with a server version that is older than what I am using.

Thanks,
Scott

---

### Post by milosz.galazka on 2008-04-24
You could try running 'ldconfig'. I don't remember ;/

---

