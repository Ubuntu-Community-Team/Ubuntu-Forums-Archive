---
title: "Problem with update"
date: 2008-02-12
forum: General Help
---

### Post by noamisback on 2008-02-12
:confused:
Hey all 
im new user in ubnutu and having problems with the updating manager
i have this massage :
[COLOR="Red"]"The underlying authorizatio mechanism (sudo) does not allow you to run this program. Contact the system administrator."[/COLOR]
which comes after this one :
[COLOR="Red"]
"Failed to run /usr/sbin/synapticFailed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '25165827' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmp4KqdGS' as user root."[/COLOR]
this errors are preventing me using the update manager and the synaptic package manager which lives me without any plugins and other important updates.
hope i was understood 
regards
noam

---

### Post by taurus on 2008-02-12
Are you using the account that you created during the installing process?  Have you made any changes to any system files like /etc/sudoers?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by noamisback on 2008-02-12
hey
yes, i am using the same account ive created during setup 
i haven't did any changes 
and the output is :[COLOR="Red"]noamisback@noam-desktop:~$ [/COLOR]

---

### Post by taurus on 2008-02-12
Run that command from that terminal and post the output here.

---

