---
title: "Accessing windows machine in the network"
date: 2007-01-29
forum: General Help
---

### Post by sudha48 on 2007-01-29
Hi, can anyone help me.......
        i have three comp , 2 windows machines and 1 linux installed in it (Ubuntu). I have installed samba in my linux machine and now  i can just view the shared folders of windows machine (by typying [COLOR="Red"]smb://192.168.0.../foldername[/COLOR]  in the URL)..But i  wanted to copy and modify those folders from my linux machine .. and also run the scripts/applications from my linux machine.How can i do that.

and i also tried "sudo smbpasswd -a sudha". Then it prompted for password i entered my password and promted for smb password and i entered..but still i cudnt able to access linux from my windows machine.Should i require to do something in windows to enable it???

any solutions would be appreciated.

---

### Post by hal10000 on 2007-01-29
Here is a docu on how to configure smba server: [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html)

---

