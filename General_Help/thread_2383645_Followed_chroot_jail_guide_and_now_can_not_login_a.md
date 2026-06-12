---
title: "Followed chroot jail guide and now can not login as putty closes soon after"
date: 2018-01-27
forum: General Help
---

### Post by Pandee on 2018-01-27
Hello,

I have followed this guide to setup a chroot user [https://www.cyberciti.biz/faq/debian-ubuntu-restricting-ssh-user-session-to-a-directory-chrooted-jail/](https://www.cyberciti.biz/faq/debian-ubuntu-restricting-ssh-user-session-to-a-directory-chrooted-jail/)

But now I can't login at all as putty closes and says the connection was refused.

Note:

-Ubuntu 14.04
-ssh status is running
-UFW allows port 22

Also:

I did a

> sshd -t

And says it "Could not load host key: /etc/ssh/ssh_host_rsa_key"

I then did
> ls -al /etc/ssh/ssh*key
And the keys are there

Thanks!

---

