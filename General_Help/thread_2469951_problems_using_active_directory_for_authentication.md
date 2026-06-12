---
title: "problems using active directory for authentication service"
date: 2021-12-15
forum: General Help
---

### Post by 7-vric-8 on 2021-12-15
I've tried to configure 20.04 and 21.10 to work with active directory and no joy.

in /var/log/sssd/sssd_sa.com.log I get the following as a common repeating error

(2021-12-15  1:24:33): [be[sa.com]] [sss_ldap_init_sys_connect_done] (0x0020): ldap_init_fd failed: Bad parameter to an ldap routine. [22][cldap://dc01.sa.com:389]
(2021-12-15  1:24:33): [be[sa.com]] [sdap_sys_connect_done] (0x0020): sdap_async_connect_call request failed: [5]: Input/output error.
(2021-12-15  1:24:33): [be[sa.com]] [ad_cldap_ping_done] (0x0040): Unable to get site and forest information [2]: No such file or directory

(2021-12-15  1:46:59): [be[sa.com]] [be_nsupdate_done] (0x0040): nsupdate child execution failed [1432158240]: Dynamic DNS update failed
(2021-12-15  1:46:59): [be[sa.com]] [ad_dyndns_sdap_update_done] (0x0040): Dynamic DNS update failed [1432158240]: Dynamic DNS update failed
(2021-12-15  1:46:59): [be[sa.com]] [be_ptask_done] (0x0040): Task [Dyndns update]: failed with [1432158240]: Dynamic DNS update failed

my google fu has failed me.  any suggestions?

---

### Post by HermanAB on 2021-12-15
Eew… I’m just wondering whether you are studying for a career on the Dark Side, or are you just a sucker for punishment?

Active Directory is LDAP, DNS and Kerberos done wrong.  That awkward brotherhood suffers from case sensitivity, dynamic DNS bugs, instability, a lack of a real time server and missing documentation. 

One important tip: Don’t try to modify anything - delete a faulty entry and make a new record.

You can find some documentation on Active Directory in online Samba server guides, since it is frequently used with AD.

---

### Post by 7-vric-8 on 2021-12-15
I am a sucker for punishment. A total glutton. Suffering thousands of cuts from Windows ME CDs.

Seriously, I am trying to work with TruNAS set up with A/D for the Windows machines in the office. It won't let me use NFS unless the Linux machine as part of the  active directory domain. Yup, screwed again by Windows.

---

### Post by rsteinmetz70112 on 2021-12-15
So you already have an AD Server and you are trying to get the Linux server to join the AD Domain?
What have you done so far?

Most references use realmd to make that connection. 
This article [https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/) seems to have a fairly complete description of how to do it.

---

### Post by TheFu on 2021-12-15
I haven't seen/touched AD since 2008.  We switched to OpenLDAP for centralized user management around 2008. It was a pain too mainly because the LDAP server was part of Zimbra and with each update, I had to remove the POSIX schema, do the upgrade, then put the POSIX schema back.  It was a pain for me and users. Zimbra has a mode that allows it to point at an external LDAP server for users and authentication. I've not used that. 

For a few years, the "best answer", for certain values of "best" was to setup FreeIPA on CentOS and use that monster to handle users. They ported the FreeIPA to Debian/Ubuntu for about 6 months, then let it die again.  FreeIPA is what happens when 50 F/LOSS projects are used to make 1 overall solution.  There must have been 100 different languages used. It was ugly.  RH seems to have abandoned it and has been pushing their commercial directory server the last few years. I've not touched it or FreeIPA.

Didn't 21.04 introduce integrated AD? [https://ubuntu.com/blog/ubuntu-21-04-is-here](https://ubuntu.com/blog/ubuntu-21-04-is-here) yep.  At install time, they imply that connecting an Ubuntu system into an AD forest was possible.  > 
Active Directory: Bridging the gap between system administrators and Linux developers

Ubuntu machines can join an Active Directory (AD) domain at installation for central configuration. AD administrators can now manage Ubuntu workstations, which simplifies compliance with company policies.

Ubuntu 21.04 adds the ability to configure system settings from an AD domain controller. Using a Group Policy Client, system administrators can specify security policies on all connected clients, such as password policies and user access control, and Desktop environment settings, such as login screen, background and favourite apps.

Since AD doesn't map 1-for-1 with Unix management, there are many gaps where a real admin would use scripts or Ansible to configure in a consistent way.  People acting like Group Policy is some magical thing don't know ansible or scripts that Unix admins have used for 40+ yrs to manage all their workstations and servers. That's my guess.

Canonical has given up on doing anything but connecting into AD, it seems.  What has been missing from all Linux systems was a purpose-built, built-in, user/group/netgroup LDAP solution that supports POSIX fields for 25 yrs. It is embarrassing really.  Since NIS was deemed too poor at security to be used anymore in the late 1990s, something that should be trivial to setup on clients has become much too hard.

As for how to connect 20.04 into AD, IDK. For some reason, I thought sssd was the normal method. Bet there is a guide for that on help.ubuntu.com. [https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd)  Google found that.

With NFS, centralized user/group management is a blessing for non-trivial situations. For 5 users, ensuring uid/gid map exactly isn't too hard, but many more than that number and it becomes a pain.

---

### Post by 7-vric-8 on 2021-12-15
> **rsteinmetz70112 said:**
> So you already have an AD Server and you are trying to get the Linux server to join the AD Domain?
What have you done so far?

Most references use realmd to make that connection. 
This article [https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/) seems to have a fairly complete description of how to do it.

I decide to focus on using 21.10 since it had the most current  implementation of whatever the hell Ubuntu is going to do for active directory integration.

During installation, I set up the realm, used my administrator account to join into the realm  and it seems like everything worked but I couldn't login. I dug through the log files and found the error messages I posted earlier but apparently they don't mean much. Thanks to your prompting, I looked closer at the documentation, deeper into the realm data and found the following

> ubuntu@ubnt4:~$ realm list
sa.com
  type: kerberos
  realm-name: SA.COM
  domain-name: sa.com
  configured: kerberos-member
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  **login-formats: %U@sa.com**
  login-policy: allow-realm-logins

The bolded line completely explains why I couldn't login. I was trying to login with username 7-vric-8 but when I used [EMAIL="7-vric-8@sa.com"]7-vric-8@sa.com[/EMAIL], I was able to login and it created /home/7-vric-8@sa.com for home directory. Seeing the login format triggered memory of something I read in [https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd). search for "*SSSD Configuration*". I found the following explanation:
> 
[LIST]
[*]home directory: it’s by default /home/<user>@<domain>. For example, the AD user john will have a home directory of /home/john@ad1.example.com 
[*]use_fully_qualified_names: users will be of the form user@domain, not just user. This should only be changed if you are certain no other domains will ever join the AD forest, via one of the several possible trust relationships 
[/LIST]

since I was only going have one AD forest, I figured I could go in and hack on the sssd.conf file and sure enough, it worked. I change the following lines:[INDENT]fallback_homedir = /home/%u@%d ==> fallback_homedir = /home/%u
[/INDENT]
[INDENT]use_fully_qualified_names = True  ==>use_fully_qualified_names = False
[/INDENT]

no more @sa.com needed on login or found in the home directory. I need to do a little more learning and understand the implication of those changes but for now, it's working. Now I need to figure out how to deal with NFS and the Windows uid/gid in the linux environment . see:  

> uid=1329224634(7-vric-8) gid=1329200513(domain users)

I'll update this after I figure out NFS

---

### Post by 7-vric-8 on 2021-12-15
> **TheFu said:**
> 
Didn't 21.04 introduce integrated AD? [https://ubuntu.com/blog/ubuntu-21-04-is-here](https://ubuntu.com/blog/ubuntu-21-04-is-here) yep.  At install time, they imply that connecting an Ubuntu system into an AD forest was possible.  

Since AD doesn't map 1-for-1 with Unix management, there are many gaps where a real admin would use scripts or Ansible to configure in a consistent way.  People acting like Group Policy is some magical thing don't know ansible or scripts that Unix admins have used for 40+ yrs to manage all their workstations and servers. That's my guess.

Canonical has given up on doing anything but connecting into AD, it seems.  What has been missing from all Linux systems was a purpose-built, built-in, user/group/netgroup LDAP solution that supports POSIX fields for 25 yrs. It is embarrassing really.  Since NIS was deemed too poor at security to be used anymore in the late 1990s, something that should be trivial to setup on clients has become much too hard.

As for how to connect 20.04 into AD, IDK. For some reason, I thought sssd was the normal method. Bet there is a guide for that on help.ubuntu.com. [https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd)  Google found that.

With NFS, centralized user/group management is a blessing for non-trivial situations. For 5 users, ensuring uid/gid map exactly isn't too hard, but many more than that number and it becomes a pain.


You hit on most of my sore points. Linux distributed authentication is a freaking dog's breakfast.  NIS was the right level of complexity and functionality that solved 95+ percent of the needs. If the security model wasn't screwed up, I still be using it today because it just worked. This AD and clones crap is crazy making. Although I will point out that both Univention and Jumpcloud solve this problem better than AD solutions ever could. Unfortunately, I'm stuck with AD because it's too deeply embedded to be able to replace with something better.

I found the service-sssd document on my own when I started this journey but sometimes you need to learn a whole bunch of other things for the original document to make sense. I am annoyed that canonical started something and then dropped the ball on integration with AD. 

I've made some progress, I can login but I haven't figured out how to fix the UID GID problem. Apparently active directory systems don't replicate the Linux model of having user and group names be the same (Fred/Fred)

---

### Post by HermanAB on 2021-12-16
From my limited experience, the first thing is to ensure that all machines have network time, point the DNS client at the AD DNS server, then get the kerberos client to work and after that the rest should be easy.  Remember that all these MS services are strangely case sensitive and avoid any funny characters in names, since UNIX and Windows have different ideas about which ones are valid. Test kerberos and authentication with the command line utilities, so that you can see the error messages.

---

### Post by TheFu on 2021-12-16
> **7-vric-8 said:**
>  
I've made some progress, I can login but I haven't figured out how to fix the UID GID problem. Apparently active directory systems don't replicate the Linux model of having user and group names be the same (Fred/Fred)

The groupnames matching the username by default is something I've only seen in home environments.  In businesses, that isn't done. Rather, everyone gets placed into a group specific to their team or, lacking that, they only get put into the "users" group.  The default umask is 022, not 002. Some places, the teams make their umask 077 by default and only expect team shared files to be located outside HOME directories.

Usernames should be all lowercase, BTW. Same for groupnames.

Having a group match the username has always bothered me. I never saw the point. Slackware didn't do that in the 1990s. The first time I remember seeing it was with Ubuntu around 2006. I hadn't used any Debian-based distro before then, so ignorance is certainly possible.

I don't see why NFS should have any issue with the uids provided by AD in the example above.  The main risk is that NFS does get confused when users are in too many groups. I think 15-20 is the practical limit where crazy things start happening. I've never seen this myself.

---

### Post by HermanAB on 2021-12-16
Again, note that Windows and Linux handle case differently.  If a name is defined in lower case in Linux, the result is a case insensitive name.  That is why you can type [http://GooGle.CoM](http://GooGle.CoM) and it will work.  Not quite so in Windows.  So if names are defined in mixed or upper case in AD, then you better copy it exactly like that on Linux.  Some of the AD utilities come from BSD and behave as one would expect and some not.  It is a dogs breakfast.

---

