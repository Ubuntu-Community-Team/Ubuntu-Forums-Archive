---
title: "How do I set up anonymous access in ProFTPD?"
date: 2006-08-03
forum: General Help
---

### Post by shingalated on 2006-08-03
How do I set up anonymous access using proftpd so that anyone can log in and see the directory /home/ftp/files/Anonymous, with the username anonymous and any email address for a password?
I tried the section below, but that would not work.

<Anonymous ~ftp>
User ftp
Group nogroup
UserAlias anonymous ftp
MaxClients 10
RequireValidShell off #I personally think its safer for user ftp to have no shell, hence this directive
DisplayLogin welcome.msg
DisplayFirstChdir .message
AllowOverwrite off #If they up it, you have a right to see it before they whack it
PathAllowFilter "^[-A-Za-z0-9._+]*$" #Only allow matches to this regexp for uploads
PathDenyFilter "(^|/)[-.]" #This restricts lame leading characters on uploads that
#might otherwise be permitted by the ruleset above
AllowFilter "^[a-zA-Z0-9 .,/_+\-]*$" #Only allow COMMANDS matching this regexp
</home/ftp/files/Anonymous>
Umask 0133 0444
<Limit RMD DELE SITE_CHMOD RNFR>
DenyAll
</Limit>
<Limit CWD MKD STOR RETR STAT>
AllowAll
</Limit>
</Directory>
<Directory /home/ftp/files/Anonymous>
Umask 0133
<Limit MKD RNFR DELE RMD SITE_CHMOD>
DenyAll
</Limit>
<Limit CWD RETR STAT>
AllowAll
</Limit>
</Directory>
</Anonymous>

---

