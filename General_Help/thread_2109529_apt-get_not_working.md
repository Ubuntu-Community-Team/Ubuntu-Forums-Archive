---
title: "apt-get not working"
date: 2013-01-27
forum: General Help
---

### Post by jacob-heller on 2013-01-27
Hello all,

When I try to install a package (in this case, Postfix -- sudo apt-get install postfix), I get these errors:

> Err [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) maverick-updates/main postfix i386 2.7.1-1ubuntu0.2
  403  Forbidden
Failed to fetch [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.1-1ubuntu0.2_i386.deb](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.1-1ubuntu0.2_i386.deb)  403  Forbidden

When I try to do sudo apt-get update:
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

I am running 10.04 LTS. Is that the reason why this isn't working?  I'm a little worried about upgrading, given that a live we app is running on the server...

What should I do?

Thanks!
Jake

---

### Post by deadflowr on 2013-01-27
You'll find this a common occurence.

So in short, 10.10 is dead and no longer supported.

You'll either need to upgrade to supported release or convert your sources.list

To convert read this page:

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

Edit: You say you're running 10.04, but the repos listed are 10.10.

10.10 is the maverick release.

If you were running 10.04, then it would be the lucid release.

---

### Post by papibe on 2013-01-27
Hi jacob-heller.

Sometimes repositories are down for maintenance. If it is urgent, wait a couple of hours and then try again.

There's an alternative: set the repositories download server that is closer (in terms of pings). Take a look at this [tutorial]("https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server"), specially the sub section called 'Best Server'.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by jacob-heller on 2013-01-27
@deadflowr -- you're right, I have Maverick (10.10). 

I tried adding those lines to sources.list, and was able to install postfix afterwards, which is great.

If I were to upgrade to the latest LTS (12.04?), would I lose everything I installed (such as Postfix?)

Thanks for your super quick reply, btw.

---

