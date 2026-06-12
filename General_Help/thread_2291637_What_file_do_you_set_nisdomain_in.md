---
title: "What file do you set nisdomain in?"
date: 2015-08-21
forum: General Help
---

### Post by eclay on 2015-08-21
Hello,

I've been searching today to find out how one can set the nisdomainname.  I've found information on the following page that states you should have the hostname in /etc/hostname and an entry in /etc/hosts file.

[http://manpages.ubuntu.com/manpages/lucid/man1/domainname.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/domainname.1.html)

It also mentions that hostname -y should display the nisdomainname.  When I execute this on my system I get the following error.

# hostname -y
hostname: Local domain name not set

hostname returns the correct systems name and hostname -d returns a valid domain name.  I'm looking for a method to set nisdomainname in a config file that will make this setting persistent across system reboots.

The reason I'm looking for this is to trouble shoot issues with sudo and ipa.  The following page mentions nisdomainname needs to be set.

[http://www.freeipa.org/page/Troubleshooting#Troubleshooting_scenarios](http://www.freeipa.org/page/Troubleshooting#Troubleshooting_scenarios)

     * Make sure that NIS domain name matches your domain: nisdomainname

---

### Post by TheFu on 2015-08-21
NIS domainname is different from the normal domainname set in /etc/domainname and with the domainname command.  If you aren't running NIS (and nobody should since 1995), you don't need this.  The security of NIS is extremely poor and because of what it controls, completely unacceptable to be used these days.

So ... if you still want to setup NIS, there is a guide which explains the server-side and client-side stuff.  All the freeIPA stuff I found that referenced NIS was for migrating accounts FROM NIS to FreeIPA.  That troubleshooting note seems out of place to me ... however .... 

I haven't run NIS since the mid-1990s.
I have never used FreeIPA. We only run LTS Ubuntu here.
For LDAP-based authentication, I'm positive that NIS domainname is not necessary.

Guess I'm confused why NIS anything is involved. Is there a freeIPA setup guide you are following so we can have some context?

Or am I missing the issue completely?

---

### Post by jbwillia on 2015-09-09
It took me forever, but I finally found the answer to this very annoying problem! It was in the last place I would have expected too: right at the top of /etc/sysctl.conf of all places...

It gets set by the setdomainname() system function. And by the way Fu, this is the domainname you were looking for; you just didn't realize it! ;) Debian (and thus Ubuntu) pulled a fast one on us; used to, they followed the old Solaris NIS standard of taking this from /etc/defaultdomain ... Yet, we still set set the hostname via /etc/hostname in an upstart job called hostname rather than rely on the entry in /etc/hosts based on resolvconf's order of interface precedence... #SMH, not my problem, lol

**[setdomainname]("http://manpages.ubuntu.com/manpages/trusty/man2/setdomainname.2.html")**(2)

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3
```

Why does it matter, though, you ask? Because it's a libc6 system library function intertwined with its counterpart **[gethostname]("http://manpages.ubuntu.com/manpages/trusty/man2/gethostname.2.html")**(2),  and there are still a lot of things that reference it (being a part of  the libc6 library and all). Things get confusing when you don't know where conflicting variables are are coming from. But alas, it wasn't the root cause of my SSO problems - it just made for some ugly logs and such. It's one less thing to bang my head over though.

---

