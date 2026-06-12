---
title: "Evolution Error: &quot;Error while Storing folder '(foldername)'&quot;"
date: 2008-03-08
forum: General Help
---

### Post by Th3Professor on 2008-03-08
Hi,

Quick note - this is not an Error regarding the entire Inbox, it is only regarding one specific folder within the Inbox. The other folders are functioning just fine.

This is the issue that's got me puzzled...

In the Evolution Email program, within the Inbox section, I have several subdirectories or folders. One is "Family". When I click on that folder, then click on another folder, I get this error message:

```

Evolution Error
Error while Storing folder 'Inbox/Family'.
Summary and folder mismatch, even after a sync

```

I can't do anything but click "OK".

The odd thing is, I can click on any other folder (subdirectory of Inbox, just like 'Family' is a subdir of it), then click on *another* folder - and I don't get the error window popping up.

It appears my 'Family' folder/subdirectory is still functioning just fine, as I can access the mail in it... it's just popping up that silly error.

Any ideas on how I can fix that? (It's not the entire Inbox, just the 1 subdirectory.)

Thank you! :)

---

### Post by boeing777 on 2008-03-08
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014)

---

### Post by Th3Professor on 2008-03-08
Oh wait nevermind! :) I found a thread with the solution:
[http://ubuntuforums.org/showthread.php?t=106191&highlight=%22Error+storing+folder+INBOX%22](http://ubuntuforums.org/showthread.php?t=106191&highlight=%22Error+storing+folder+INBOX%22)

It looks like the link (boeing777) provided actually discusses similar steps (involving the "[foldername].ev-summary" file).

Thanks for the link still, it helped confirm the steps necessary.

:)

---

