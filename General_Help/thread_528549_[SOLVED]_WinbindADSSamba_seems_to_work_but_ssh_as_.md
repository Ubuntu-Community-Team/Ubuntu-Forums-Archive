---
title: "[SOLVED] Winbind/ADS/Samba seems to work but ssh as any user fails"
date: 2007-08-18
forum: General Help
---

### Post by herald on 2007-08-18
OK so I've got pretty much everything working.  The problem is in the common-auth or something.

I've got it to where I can do the wbinfo -u and list the users, and wbinfo -g will list the groups, yadda yadda.  However, if I try and ssh into the system running winbind and samba, I get the following:

Aug 17 23:40:21 localhost pam_winbind[13097]: user 'chaos+herald' granted access
Aug 17 23:40:21 localhost pam_winbind[13097]: user 'chaos+herald' granted access
Aug 17 23:40:21 localhost sshd[13097]: Failed password for chaos+herald from <ipaddress> port 54504 ssh2

and at the login prompt I get access denied.

Has anyone seen this before??  The Kerberos installed and configured fine, I can get a kerb ticket.  The Winbind finally works, and I have bound to the w2k3 server and I can do the wbinfo mentioned above.  However, I can't login either from console or from ssh!!!  Killing me!!!  PLEASE HELP!!!


{Addendum}
So after messing around for an hour, I found myself totally locked out of the system.  It wouldn't accept any Domain accounts, it wouldn't accept any local accounts, I couldn't SU I couldn't sudo.  I have isolated the problem to my /etc/pam.d/common-auth file, where I'm implementing pam_winbind.so to authenticate via the ADS.  When I comment that out, I can once again login locally.

I really hope these symptoms ring a bell, because I know I'm SO close to getting this to work and it's killing me!!  I've got about 300 GB worth of data I need to pull off a tape library, but I have to be able to access these shares via AD credentials first before I can start dumping from tape.  HELP! And TIA!

-Herald

---

### Post by HermanAB on 2007-08-18
See this:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

You need to edit the SSH Pam file.

Cheers,

Herman

---

### Post by herald on 2007-08-18
> **HermanAB said:**
> See this:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

You need to edit the SSH Pam file.

Cheers,

Herman

Herman, you are the MAN!

The pam config files in my pam.d were very conveniently referencing common-auth and common-account, et al, and that was where I had my pam_winbind.so links.  The real kicker of all this was, all the HOWTOs I'd seen had either pam_winbind or pam_unix as required instead of sufficient.  The real key to all of this is to have both pam_winbind AND pam_unix as sufficient, so that a posititive authentication from either/or will work.

If one configures pam_winbind as required and pam_unix as sufficient, then regardless of whether or not one authenticates with pam_unix, they MUST successfully authenticate with pam_winbind.  If you can't do that, you'll be screwed....This would also be true vice/versa (as was my case) with pam_unix required and pam_winbind sufficient.

(this was subtly buried in example pam configs in the article Herman graciously referenced)

The sufficient/sufficient configuration allows either a Windows AD account or a Linux Local account authenticate.  This will (as was mentioned in one of the 30+ articles I read) send lots of spew to log files, but that can be filtered and/or ignored.

I'm sure Herman knows all this (many thanks again, btw) but the above stuff is for anyone else who is seeing one side of authentication work but still not being granted access (IE Accepted password for <domain+user> and then no such user for sshd or login, or also a password failed for sshd or login), while every darn thing in the system seems to be working perfectly otherwise.  

I hope all this makes sense, it's about 4:10 in the AM, I've been up all night beating away at this, and my thoughts aren't exactly clear and organized.   I'm so thrilled to have this working I'm going to have to work hard at not unracking my server and installing the tape library controller...Working on server racks at 4 AM is Bad...Very Bad!

I would also just like to say that the Ubuntu community is BY FAR the most helpful, active, and cooperative Linux community there is, and I've worked with RedHat, SuSe, Mandrake, and several others.  Thanks everyone!!!

-Herald

---

