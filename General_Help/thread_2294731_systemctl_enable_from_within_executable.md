---
title: "systemctl enable from within executable"
date: 2015-09-12
forum: General Help
---

### Post by roland-logikalsolutions on 2015-09-12
I have question about systemctl enable.

I have a service srcript which gets copied into the correct location by an executable which is owned by root and has sticky bit set. No matter how I try to execute "systemctl enable my.service" it always returns 1.

Executing the same command from the command line under sudo and reboot the computer the script runs as expected.

Here is my question. In the terminal window when enabling the service it displays a message about creating a link. Is that really all it does? Can I just create the link from within my priviledged executable and the service will run at system restart?

I haven't tried this yet because I have a sinking feeling there are other knobs and levers which need tweaking.

Thanks,

---

### Post by roland-logikalsolutions on 2015-09-13
Yes, hacking in the symbolic link does work. Just to be safe the un-install shell script calls systemctl disable my.service

---

