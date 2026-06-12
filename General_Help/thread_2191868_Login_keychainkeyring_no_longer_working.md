---
title: "Login keychain/keyring no longer working?"
date: 2013-12-04
forum: General Help
---

### Post by alanhoyle on 2013-12-04
I've been a long-time Ubuntu user.  I'm currently on 13.10 on a PC.  

I use a public/private key pair to ssh to various servers at my office, and until recently I was able to accomplish this without too much effort.  The first time I tried to SSH (or after a long break), it would prompt me for my private key passphrase for /home/username/.ssh/id_rsa.  Now, it prompts me every time.  I seem to have an ssh-agent running, and keychain finds it:

[FONT=Lucida Console]alanh@lbg-alanh:~$ ps x |grep ssh-agent |grep -v grep
 9186 ?        Ss     0:00 ssh-agent
alanh@lbg-alanh:~$ keychain

 * keychain 2.7.1 ~ [http://www.funtoo.org](http://www.funtoo.org)
 * Found existing ssh-agent: 9186

[/FONT]

Also, I recall being prompted at login for my keychain password, but that hasn't happened the last few logins.  Can anyone point me in the right direction for how to make this work again?

---

