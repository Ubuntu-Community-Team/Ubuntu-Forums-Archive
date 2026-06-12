---
title: "During SSH password won't unlock private key"
date: 2013-07-12
forum: General Help
---

### Post by strange_cathect on 2013-07-12
I'm using Ubuntu 13.04. 

I'm trying to push something with git over an SSH connection. But, out of nowhere, I get a message that asks me to "Enter password to unlock private key." It asks for the password for my username on the ubuntu login. But it will not unlock, even when I give it the correct password. It won't accept blank either. So it is impossible for me to send my data through SSH.

What the heck?

---

### Post by Habitual on 2013-07-13
Out of "nowhere" since when and where is the message coming "from" during your intended usage?
Before connecting to the (remote?) host or after connecting to it?
Did you give it a password?
Are you using this format to connect?
```
 ssh -i /home/jj/.ssh/my_key user@host
```

else I think if you don't it will default to /home/$user/.ssh/id_rsa or whatever the "[default]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")" key is in the .ssh directory.

---

