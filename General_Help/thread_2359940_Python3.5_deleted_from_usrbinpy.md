---
title: "Python3.5 deleted from /usr/bin/py*"
date: 2017-04-29
forum: General Help
---

### Post by paramx on 2017-04-29
Hi,

I upgraded to 16.04 3 weeks back. In my /usr/bin I have all python versions from 2.7 to 3.5. By default /usr/bin/python pointed to python2.7. I tried to make it point to python3.5. Went through some tech site isntructions and ended up creating a softlink /usr/bin/python3.5 -> /usr/local/bin/python .. /usr/local/bin/pytho was not existing. In an attempto clean up /usr/bin/python3.5 link, I also ended up deleting /usr/bin/python3.5 executable. I tried to upgrade python or my distribution but still getting different errors. Attached are different screenshots. Can you please help me resolving this? I am not able to open gnome-terminal because of this as well. 

Can you please help resolving this?

Thanks,
ParamX

:(

---

### Post by dragonfly41 on 2017-04-30
Miniconda might help you in controlling use of python versions .. certainly safer than hacking links

[https://conda.io/miniconda.html](https://conda.io/miniconda.html)

But it does add in an extra layer of admin which you might not require.

---

