---
title: "setting up SSH"
date: 2016-02-07
forum: General Help
---

### Post by devlin3 on 2016-02-07
Hi there,

I'd like to set up a remote server using SSH. I am following the instruction to configure SSH from this site:

[http://www.htpcbeginner.com/install-ssh-server-on-ubuntu-1204/](http://www.htpcbeginner.com/install-ssh-server-on-ubuntu-1204/)

After following those directions to edit the SSH, it tells me to restart the SSH using a terminal command. I assume that before I do this, I must exit the editing menu. When I hit ^X to exit, I select "Save modified buffer" to save my changes, but then it asks me where to save as such:
> File Name to Write: /etc/ssh/sshd_config                                        
^G Get Help         M-D DOS Format      M-A Append          M-B Backup File
^C Cancel           M-M Mac Format      M-P Prepend

I did back up the SSH per the instructions at the link above, but I'm not exactly sure which File Name I should write to.

Thank you in advance for taking the time to read and respond.

---

### Post by sohlinux on 2016-02-07
save it in the same place /etc/ssh/sshd_config

---

### Post by deadflowr on 2016-02-07
In terms of ssh 101: don't use passwords.
Use keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by devlin3 on 2016-02-07
> save it in the same place /etc/ssh/sshd_config

Ah ok so /etc/ssh/sshd_config is the file name. And if I hit enter, it should be saved just fine?--I was assuming that I would have to enter one of the commands to save it in MAC or DOS or backup.

> In terms of ssh 101: don't use passwords.
Use keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Thanks, I will look into that. Would love any advice on improving security.

---

### Post by sohlinux on 2016-02-07
it will save it in the same place /etc/ssh/sshd_config, just hit enter then restart ssh

---

### Post by devlin3 on 2016-02-07
> **sohlinux said:**
> it will save it in the same place /etc/ssh/sshd_config, just hit enter then restart ssh

done, that appeared to work. thanks

---

### Post by sohlinux on 2016-02-07
> **devlin3 said:**
> done, that appeared to work. thanks

good news, pls mark the thread SOLVED

---

### Post by devlin3 on 2016-02-07
I will do that in the future. I'm new to the forums, so I apologize for any future decorum violations.

I marked the thread unsolved again because when I type in the command 

> username@laptop:~$ ssh-copy-id username@remotehost

It takes quite a while to execute it, and then the output reads:

> /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: ERROR: ssh: connect to host remotehost port 22: Connection timed out

I figured marking the thread unsolved would be preferable to potentially spamming General Help with future questions I may have in setting up an SSH

---

### Post by CaptainMark on 2016-02-08
Just to clarify, and hopefully not to patronise, sorry if it does but you never quite know other peoples knowledge levels, what might seem obvious to one is hard to another.
You aren't literally typing username@remotehost are you? You need to replace username with your username and remotehost with your server ip address or hostname.
So mine is mark@192.168.0.10 or mark@desktop because that name is tied to that IP in ~/.ssh.config so if you log into SSH successfully with
```
ssh devlin@desktop
```then you just change it to ```
ssh-copy-id devlin@desktop
```

---

### Post by deadflowr on 2016-02-08
Did you set a different port than the default port 22?
If so, per the reference in the link I posted to what you need to do in such cases:
```
ssh-copy-id  "name@remotehostname-or-ipaddress -p ####"
```
note the quotes are required, and change the port number #### to whatever port number you set in the config file.
See if that works.

---

### Post by devlin3 on 2016-02-08
CaptainMark, I am very much a beginner in many aspects, with occasional forays into more intermediate tasks. I did type "devlin@remotehost" which was the cause of that problem. I replaced "remotehost" with the actual name of the remote host. Thanks for taking the time to help.

deadflowr, once I fixed the above problem, I did run into the problem you mentioned, but I did some reading and found the solution before getting a chance to read your post. Thanks to you as well.

I will be marking this thread as solved until if and when I run into another hiccup.

---

