---
title: "Is there a way to authenticate to Active Directory without joining domain?"
date: 2015-05-14
forum: General Help
---

### Post by cableguy414 on 2015-05-14
I know that there are ways to set up authentication to AD (Winbind, Likewise, Centrify, etc.), but they all require you to actually join the domain.  Is there a way to just authenticate against the domain without joining?  I know that it must be possible, because I've seen other web applications/appliances do it all the time.  

Maybe through LDAP?

I've tried searching, but the only hits I get are mainly using the above listed options.  I haven't seen any specific "How-tos" on getting Linux/Ubuntu to authenticate to Active Directory using strictly LDAP.

Any help would be appreciated.

I'm running Ubuntu 14.04, by the way.

Thanks.

---

### Post by R.P on 2015-05-14
CableGuy,

I know of two methods using Centrify that can authenticate you against AD without making your system an actual member of AD.

For example,
You can download their solution here:  [http://www.centrify.com/express/linux-unix/download/](http://www.centrify.com/express/linux-unix/download/) 
Gunzip the tarball and install it (e.g.  dpkg -i centrifydc-5.2.2-deb5-x86_64.deb)
At this point the agent is installed, but you won't be a "member of ad" until you run the adjoin command.

The options you have at this point are:

**Kerberos**
Use Centrify's MIT Kerberos tools  (these tools are in /usr/share/centrifydc/kerberos/bin).
All you need to do is to have a krb5.conf file from a system that belongs to the domain (or you can join, copy the krb5.conf file created by centrify, and then leave the domain)

Example:

# not joined to any domain
[FONT=courier new]$ adinfo
Not joined to any domain
Licensed Features: Enabled[/FONT]

# Authenticate to AD with a user named Bart using Kerberos

[FONT=courier new]$ KRB5_CONFIG=/etc/krb5.conf.1  /usr/share/centrifydc/kerberos/bin/kinit bart.simpson
Password for [EMAIL="bart.simpson@YOURDOMAIN.COM"]bart.simpson@YOURDOMAIN.COM[/EMAIL]:
$ /usr/share/centrifydc/kerberos/bin/klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [EMAIL="bart.simpson@YOURDOMAIN.COM"]bart.simpson@YOURDOMAIN.COM[/EMAIL]

Valid starting     Expires            Service principal
05/14/15 18:50:21  05/15/15 04:50:25  krbtgt/YOURDOMAIN.COM@YOURDOMAIN.COM
        renew until 05/15/15 18:50:21
[/FONT]
If you have Kerberized applications (like Hadoop) you can use the Kerberos TGT to obtain service tickets.  Note that the /etc/krb5.conf.1 was the working file from a previous join.

**LDAP**

Here you use a system with Centrify that is joined to the domain and it's running Centrify's LDAP Proxy  (Basically an OpenLDAP server compiled to use Centrify's assets).
This video gives you a walk-through:  [https://www.youtube.com/watch?v=l-3zcNcCEGI](https://www.youtube.com/watch?v=l-3zcNcCEGI) 

Once you have the Proxy running, you can use unjoined Unix, Linux, Mac, appliances or apps as LDAP clients.  The cool thing about this is that you don't need to be "joined" to AD and you have exposed AD information via a proxy.
You can authenticate against it (use LDAPS).

Here's an example using a NetApp appliance as a client of this proxy:  [http://centrifying.blogspot.com/2014/07/business-problems-how-to-solve-issue-of.html](http://centrifying.blogspot.com/2014/07/business-problems-how-to-solve-issue-of.html) 

I hope this is useful,

R.P

---

### Post by tornadof3 on 2015-05-15
Do you mean authenticating for the purposes of logging-in users to a linux session, or for other purposes?
We use ActiveDirectory as an authentication source all the time in our custom-designed PHP websites running on linux servers which are in no way part of a windows 'domain' (but they are on the same LAN).... it is very easy. Maybe this will help:

The code below will authenticate to a Microsoft ActiveDirectory server on the local network. It will determine whether supplied username/password is in the 'webaccess' (use the web application but no special privileges', 'webaccessAdmin' (use web application and do admin) or disallow. Users are in the OU=Users,DC=EXAMPLE,DC=COM (edited) DN and the relevant groups you can see:
```

<?php

function authenticate($user, $password) {
    // Active Directory server
    $ldap_host = "<ip address or hostname>";
 
    // Active Directory DN
    $ldap_dn = "OU=Users,DC=EXAMPLE,DC=COM";
 
    // Active Directory user group
    $ldap_user_group = "WebAccess";
 
    // Active Directory manager group
    $ldap_manager_group = "WebAccessAdmin";
 
    // Domain, for purposes of constructing $user
    $ldap_usr_dom = "@network.internal"; // change this for your network
 
    // connect to active directory
    $ldap = ldap_connect($ldap_host);
 
 
 
    // verify user and password
    if($bind = ldap_bind($ldap, $user . $ldap_usr_dom, $password)) {
        
        // valid
        // check presence in groups
        $filter = "(sAMAccountName=" . $user . ")";
        $attr = array("memberof");
        $result = ldap_search($ldap, $ldap_dn, $filter, $attr) or exit("Unable to search LDAP server");
        $entries = ldap_get_entries($ldap, $result);
        ldap_unbind($ldap);
 
        // check groups
        foreach($entries[0]['memberof'] as $grps) {
            // is manager, break loop
            if (strpos($grps, $ldap_manager_group)) { $access = 2; break; }
 
            // is user
            if (strpos($grps, $ldap_user_group)) $access = 1;
        }
 
        if ($access != 0) {
            // establish session variables
            $_SESSION['user'] = $user;
            $_SESSION['access'] = $access;
            return true;
        } else {
            // user has no rights
            return false;
        }
 
    } else {
        // invalid name or password
        return false;
       
    }
    
}

?>

```

---

### Post by HermanAB on 2015-05-15
Yes, AD is a combination of LDAP and Kerberos.  So what you want to do is Kerberos only.  You can certainly do that.

---

### Post by cableguy414 on 2015-09-08
Sorry for the delayed reply/update.  I've been a bit distracted on a few things.  I'd like to do a couple of things actually.  My main goal is to have Ubuntu authenticate users, specifically via SSH, to AD.  However, even though I manage these Linux boxes, I don't have Domain Admin access, so I'd prefer to not have to join these to the domain if I don't have to.

A secondary goal, which recently came up, would be to possibly leverage PAM, authenticating to AD, so I can configure a TACACS+ server that will also be able to use AD.

---

