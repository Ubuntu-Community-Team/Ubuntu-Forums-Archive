---
title: "ldap pam auth not warning for password expiration"
date: 2014-03-18
forum: General Help
---

### Post by prajithpalakkuda on 2014-03-18
When users with an expired account try to log into PAM (SSH, Su, etc..) there is no warning displayed that the account is expired. The user is also allowed to login normally. 
In the slapd logging, the following message is displayed:
  
Mar 18 12:46:25 sip slapd[11790]: ppolicy_bind: Entry uid=prajith,ou=people,dc=XXX,dc=XX has an expired password: 0 grace logins

here is my ldap.conf

########
base dc=XXX,dc=XX
uri ldap://XX.XX.XX
ldap_version 3
pam_lookup_policy yes
pam_password md5
pam_password exop
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,clamav,colord,daemon,dansguardian,dnsmasq,festival,games,gnats,guest-yRzqOV,hplip,imspector,irc,kernoops,libuuid,libvirt-dnsmasq,libvirt-qemu,lightdm,list,lp,mail,man,messagebus,mysql,news,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,swift,sync,sys,syslog,usbmux,uucp,whoopsie,www-data
#######

---

