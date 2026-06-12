---
title: "krb5-user - Where, What, eh?"
date: 2005-06-24
forum: General Help
---

### Post by Philiphgray on 2005-06-24
Hello all,

Fairly new to this linux lark and totally new to ubuntu, so please excuse any stupid questions / posts in wrong places etc.

I've just done an install of ubuntu (5.04 hoary), downloaded a load of patches that it seemed to think I needed and I'm now trying to join the box to my windows 2000 active directory domain.

I've been following the guide at [https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28krb5-user%29](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28krb5-user%29) but I'm running into trouble with the kerberos setup stage.

when I try to run "apt-get install krb5-user", I get the following response:

Reading package lists... Done
Building dependency tree... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-doc
E: Package krb5-user has no installation candidate

I get a similar message to this when I try to do "apt-get install winbind", but I have managed to configure the samba/smb.conf file and I have been able to use "net ads join" to join the domain.

I also don't seem to have a /etc/krb5.conf file and trying to run kinit gives me the following message:

bash: kinit: command not found

I found a forum post that said I needed to download the krb5-user file into my apt cache and install it from there but I ended up with a load of dependancy problems after that.

I've been googling for about 3 hours on this now without any success and I'd really appreciate any help anyone can offer.

Thanks.

---

### Post by Philiphgray on 2005-06-24
Anyone?

Any Ideas?

---

### Post by Philiphgray on 2005-07-04
Still hoping for any pointers on this.  Thanks.

---

### Post by nocturn on 2005-07-04
Have you enabled universe?  I think it is in there.

---

