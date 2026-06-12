---
title: "ssh access denied to Ubuntu on local network"
date: 2004-10-30
forum: General Help
---

### Post by emperor on 2004-10-30
Can not get Ubuntu to allow an ssh connection from a computer on the local network. I have added the following to "hosts.allow" but still does not work. I have been able to connect via ssh on other distro's so what is the trick in Ubuntu?
    
    ALL: 192.168.10.0
    or tried
    ALL: 192.168.10.2
    
    I gave Ubuntu a root password and then from another client I used the following command and got the reply noted:
   
   cmd:           "ssh -l root 192.168.10.9"
   reply:  "ssh: connect to host 192.168.10.9 port 22: Connection refused"
   
   I should add that I can ssh from Ubuntu to other machines OK.
   
   ????????

---

### Post by kmf on 2004-10-30
Hmm perhaps you should make sure that you've installed  "openssh-server" in Synaptic :)

Try it ... Let us know.
Karl

---

### Post by emperor on 2004-10-30
[QUOTE=kmf]Hmm perhaps you should make sure that you've installed  "openssh-server" in Synaptic :)
 
 Try it ... Let us know.
 Karl[/QUOTE] 
 Yes  [img]http://www.ubuntuforums.org/images/smilies/icon_redface.gif[/img], that was the problem, thanks Karl! [img]http://www.ubuntuforums.org/images/smilies/eusa_clap.gif[/img]

---

