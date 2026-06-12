---
title: "Evolution 3.10.4 Hanging After Resume From Suspend"
date: 2014-05-30
forum: General Help
---

### Post by buzzingrobot on 2014-05-30
Evolution 3.10.4 on 14.04 here is hanging after a resume from suspend. (IMAP account).  I.e., it does not send/receive new mail. Mail is not retrieved/sent automatically per the interval set in preferences.   Manually starting the process -- clicking "Send/Receive" -- displays the progress bar and then Evolution hangs. Sometimes I can close it, sometimes I need to end the process.

Looking around, I see a number of bug reports over the last few years related to suspend issues, but nothing recent and nothing about this specific issue and Evolution version. 

Perhaps I just missed it, though.  Is anyone else seeing this problem, and have you fixed it?

---

### Post by ianni67 on 2014-11-13
I can confirm the issue.
Ubuntu 12.04 clean install, upgraded to ubuntu 14.04. 
DELL XPS 13 developer edfition.
Any news?

---

### Post by Ian_Young on 2014-12-30
Found [this bug which looks to be about the issue]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/897188"). Sadly, there is no indication that anyone is working on fixing it. To show the developers this is important, log in to the bug tracker and click on the "This bug affects x people" link and indicate that the bug affects you.

---

### Post by traxtopel on 2015-03-10
This idea sucks.
At least it kills evolution on resume.

sudo cat << EOF > /etc/pm/sleep.d/evolution.sh
#!/bin/bash
case "$1" in
thaw|resume)
pgrep -f evolution | xargs kill -15
;;
*)
;;
esac
exit $?
EOF

---

