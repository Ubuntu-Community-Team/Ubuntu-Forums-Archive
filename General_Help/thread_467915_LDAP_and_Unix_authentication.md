---
title: "LDAP and Unix authentication"
date: 2007-06-08
forum: General Help
---

### Post by snivek on 2007-06-08
I recently configured Kerberos and Winbind to allow Kerberos authentication against AD.  I got everything working fine and am able to login with my AD credentials.  Yippie!  I do however have some questions.  

I cannot login with my local unix account any onger.  How can I fix this?  Below is my current (pam) common-auth file.  I also have some confusion on how this is working.  pam_unix is set to required and if i log in with my AD account, wouldn't that module fail?

Second, how do I make my AD user a member of local ubuntu groups and have them stick.  Once I'm logged in I am able to add the user to a group and all is well.  After I reboot and log back in, I am no longer in the group.

[common-auth]
auth     sufficient     pam_krb5.so
auth     required      pam_unix.so nullok_secure use_first_pass

Thank you everyone!

---

### Post by defishguy on 2007-06-08
Try changing > auth sufficient pam_krb5.so
To > auth optional pam_krb5.so

Did you join the machine to the Windows domain?  If not that would explain why the machine can't pull group info from the DC until you've logged on.

The authentication schemes are executed in order, and the first successful execution is enough, that is why the mod isn't failing.

---

### Post by snivek on 2007-06-11
Thanks for the reply.  I actually was able to fix the Kerberos and Local login issue by changing my common_auth to sufficient for both modules.

To answer your question about the group issue.  Yes, the workstation is joined to the domain.

---

