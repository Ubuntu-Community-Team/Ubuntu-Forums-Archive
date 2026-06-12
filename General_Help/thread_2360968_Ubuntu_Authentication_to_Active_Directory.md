---
title: "Ubuntu Authentication to Active Directory"
date: 2017-05-10
forum: General Help
---

### Post by scalderoni on 2017-05-10
I am really hoping someone can get me over the last bit to allow Active Directory auth to work. I m on 14.04.

End of the story: 

I've configured what I believe to be everything (obviously missing something or I would not be posting). When I try to login as an AD user I get this in the auth.log and it fails to allow login. I kind of expect the first line since there is no passwd entry. pam_unix should fail. The rest is what confuses me. Lines 2-4 look like a successful auth session and then line 5 is a failure. 

```

May 10 14:42:25 oraws-pat2 login[13933]: pam_unix(login:auth): authentication failure; logname=ubuntu uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=test.user
May 10 14:42:25 oraws-pat2 login[13933]: pam_winbind(login:auth): getting password (0x00000388)
May 10 14:42:25 oraws-pat2 login[13933]: pam_winbind(login:auth): pam_get_item returned a password
May 10 14:42:25 oraws-pat2 login[13933]: pam_winbind(login:auth): user 'test.user' granted access
May 10 14:42:25 oraws-pat2 login[13933]: Authentication service cannot retrieve authentication info

```


Here are the steps I used to get this far:

```

apt-get install winbind samba libnss-winbind libpam-winbind krb5-config krb5-locales krb5-user


mv /etc/krb5.conf /etc/krb5.conf.bak


vi /etc/krb5.conf


[libdefaults]
        default_realm = TESTDOMAIN.COM


# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true


# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.
#
# Thie only time when you might need to uncomment these lines and change
# the enctypes is if you have local software that will break on ticket
# caches containing ticket encryption types it doesn't know about (such as
# old versions of Sun Java).


#       default_tgs_enctypes = des3-hmac-sha1
#       default_tkt_enctypes = des3-hmac-sha1
#       permitted_enctypes = des3-hmac-sha1


# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true


[realms]
        ATHENA.MIT.EDU = {
                kdc = dc1.testdomain.com:88
                kdc = dc2.testdomain.com:88
                admin_server = dc1.testdomain.com
                default_domain = testdomain.com
        }
[domain_realm]
        .testdomain.com = testdomain.COM
        testdomain.com = testdomain.COM


[login]
        krb4_convert = true
        krb4_get_tickets = false






kinit test.user@testdomain.COM
klist


    Ticket cache: FILE:/tmp/krb5cc_0
    Default principal: test.user@testdomain.COM


    Valid starting       Expires              Service principal
    05/09/2017 18:56:37  05/10/2017 04:56:37  krbtgt/testdomain.COM@testdomain.COM
            renew until 05/10/2017 18:56:34


vi /etc/samba/smb.conf


Add under [globaL] replace workgroup = WORKGROUP with the following:


   netbios name = -PAT2
   workgroup = testdomain
   security = ADS
   realm = testdomain.com
   encrypt passwords = yes


   idmap config *:backend = rid
   idmap config *:range = 5000-100000


   winbind allow trusted domains = no
   winbind trusted domains only = no
   winbind use default domain = yes
   winbind enum users  = yes
   winbind enum groups = yes
   winbind refresh tickets = yes


   template shell = /bin/bash




vi /etc/nsswitch.conf


Add windbind like below:


passwd:         compat winbind
group:          compat winbind


net ads join -k


    Using short domain name -- testdomain
    Joined 'test-server' to dns domain 'testdomain.com'


service winbind restart; service nmbd restart; service smbd restart


pam-auth-update


--> Ensure the Winbind NT/Active Directory authentication box is checked


echo 'session    required    pam_mkhomedir.so skel=/etc/skel   umask=0022' >> /etc/pam.d/common-account


mkdir /home/TESTDOMAIN



```

Any advice would be very appreciated!!

---

### Post by HermanAB on 2017-05-10
Hmm, making Linux work with Active Directory can be very painful.  The system is weirdly case sensitive.  Many things must be uppercase only.  The time in the host must be within 5 minutes from the time in the server, else kerberos won't work.  Test things little by little - first list the username, then try the password.

Here is a good write-up: [https://wiki.archlinux.org/index.php/Active_Directory_Integration](https://wiki.archlinux.org/index.php/Active_Directory_Integration)

---

