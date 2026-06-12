---
title: "[SOLVED] Firefox Certificate Error"
date: 2008-05-20
forum: General Help
---

### Post by CharlieNixon on 2008-05-20
I want to visit an https page, but i get this error due to an expired ssl cert:

[I]An error occurred during a connection to example.com.

Certificate key usage inadequate for attempted operation.

(Error code: sec_error_inadequate_key_usage)
[/I]

In Opera I can choose to ignore the security error and it lets me get to the page, but in FF it just says "error" and gives me no options. 

How can I ignore the expired certificate in FF?

---

### Post by CharlieNixon on 2008-05-22
in *Preferences > Advanced > View Certificates > Add exception* it looks like I could add an exception for the page I want to visit, but every time I input the URL it tries to verify it and throws the same error.

Isn't not-verifying the certificate the point of the exception?

What gives?

---

### Post by CharlieNixon on 2008-05-22
I know nobody answered my post, but just in case someone reads this later...

It looks like this is a bug in FF 3. See:
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187341](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187341)
or
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187341](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187341)
or
[http://groups.google.com/group/mozilla.feedback.firefox.prerelease/browse_thread/thread/885b8914a0cc9e80](http://groups.google.com/group/mozilla.feedback.firefox.prerelease/browse_thread/thread/885b8914a0cc9e80)

---

