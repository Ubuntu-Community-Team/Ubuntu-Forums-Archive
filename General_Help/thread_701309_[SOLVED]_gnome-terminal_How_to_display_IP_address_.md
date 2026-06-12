---
title: "[SOLVED] gnome-terminal: How to display IP address instead of hostname"
date: 2008-02-19
forum: General Help
---

### Post by abcuser on 2008-02-19
Hi,
I use Ubuntu 7.10 Desktop. In Terminal (gnome-terminal program) how to set prompt to use "IP address" instead of hostname?

I have looked into FAQ: [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#BASH-PROMPT-ESCAPE-SEQUENCES](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#BASH-PROMPT-ESCAPE-SEQUENCES)
but I can't see any settings about IP address.
Thanks,
Abcuser

---

### Post by randy78 on 2008-02-19
[http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm]("http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm")

---

### Post by seventhc on 2008-02-19
I think he's asking how to set the prompt to the ip address, not how to change the hostname.
I know if the ip is entered as hostname it would change it, but the IP might not be static. So if the real world IP changes, the prompt would be the wrong IP.

---

### Post by cdenley on 2008-02-19
Try adding this to the end of ~/.bashrc, assuming you want the ip of eth0
```

IP=`ifconfig eth0|grep inet\ addr|cut -d " " -s -f 12|cut -d : -s -f 2`
PS1='${debian_chroot:+($debian_chroot)}\u@$IP:\w\$ '

```

---

### Post by abcuser on 2008-02-20
Hi,
cdenley your solution works fine. But it looks like that this settings is only valid for local computer. If I connect with ssh to remote computer (sample: ssh -X root@192.168.1.1) then I still get hostname. It looks like this is only local settings. If I understand correctly setting above two commands should be set into each Linux box I have. This can be pain, because there are too many boxes.

Is there any way to set this settings to be valid in any Linux without writting this two commands to .bashrc file on each Linux box?
Thanks,
Abcuser

---

### Post by cdenley on 2008-02-20
The setting is a user-specific setting for bash. The file I mentioned was a user configuration. Whenever that user is using bash on that computer, it will show the ip address. The root user has it's own configuration at "/root/.bashrc". It doesn't matter if you're sitting in front of the computer or connecting with ssh, you get the same terminal. It does matter what user you log in as, since some users can be configured with a different shell than bash, or can have a different bash configuration. By the way, it is a bad idea to enable root login via ssh.

> Is there any way to set this settings to be valid in any Linux without writting this two commands to .bashrc file on each Linux box?

The bash configuration has to be changed for that user on the machine that bash is running.

---

### Post by abcuser on 2008-02-21
Hi,
thanks a lot. You helped me much to understand how gnome-terminal is displaying prompt.
Thanks,
Abcuser

---

### Post by Coort on 2008-02-21
I found in this forum this interesting how-to:
[http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

---

