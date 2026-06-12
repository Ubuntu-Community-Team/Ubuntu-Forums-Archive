---
title: "login without password"
date: 2006-11-05
forum: General Help
---

### Post by daemonoid on 2006-11-05
I'm in the process of setting up a media centre PC.

I'm looking to use the face browser on the front end to allow me to login to a number of different accounts based on what i want to do. eg having a user called 'snes' with vastly reduced privileges that will to login to zsnes.

I can handle the login scripts but i can't seem to create a user without a password. Is there a way of doing this?

---

### Post by Spano on 2006-11-05
nevermind

---

### Post by daemonoid on 2006-12-06
Anyone?

---

### Post by gate on 2007-07-15
you can alter the authentication process rather easily. 

 I was doing the same thing to let my nephews (two 6 year olds) login for games and such that I installed for them.


    here is what you do:

  edit /etc/pam.d/gdm 
  my original: 

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

my new file:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
#single click login stuff
#start
auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/oneclickusers onerr=fail
#end
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

then create a file /etc/gdm/oneclickusers
and put the usernames of your one-click users one per line.

here is the original article I used:
[http://www.ubuntuhq.com/content/view/1447/65/](http://www.ubuntuhq.com/content/view/1447/65/)

---

### Post by Ralphie on 2008-06-19
> **gate said:**
> you can alter the authentication process rather easily. 

 I was doing the same thing to let my nephews (two 6 year olds) login for games and such that I installed for them.


    here is what you do:

  edit /etc/pam.d/gdm 
  my original: 

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

my new file:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
#single click login stuff
#start
auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/oneclickusers onerr=fail
#end
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

then create a file /etc/gdm/oneclickusers
and put the usernames of your one-click users one per line.

here is the original article I used:
[http://www.ubuntuhq.com/content/view/1447/65/](http://www.ubuntuhq.com/content/view/1447/65/)


This worked great! thank you so much, it is exactly what I was looking for while setting up a system for two old folks who cant be bothered by passwords lol.

Only one error with it, 

instead of your code here:
```
#single click login stuff
#start
auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/oneclickusers onerr=fail
#end
```

use this here:
```
#single click login stuff
#start
auth sufficient pam_listfile.so item=user sense=allow file=/etc/gdm/oneclickusers onerr=fail
#end
```

It was pointing to the wrong directory in your code.

---

