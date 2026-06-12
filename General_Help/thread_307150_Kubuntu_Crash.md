---
title: "Kubuntu Crash"
date: 2006-11-26
forum: General Help
---

### Post by ScoobyDan on 2006-11-26
Hi all,

Today, Kopete will not start - it just returns a signal 11 (SIGSEGV). The Konsole output is as follows:

> kopete
QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: ListTask
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
CLIENT: SendPictureTask: Task::done()
CLIENT: SendPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: StatusNotifierTask
QGArray::find: Index 0 out of range
KCrash: Application 'kopete' crashing...

Any ideas what could be causing this? Nothing has changed since yesterday (no new installs). I have "apt-get update"'d and "apt-get upgrade"'d, but nothing new was installed. I have purged and re-installed Kopete, but still no joy :(

Any ideas?

Daniel

PS - Running on a fully-updated Kubuntu 6.10

---

### Post by cvmostert on 2007-04-14
I have exactly the same problem upon first start of kopete... after that it starts up sometimes... have you found a sollution yet?

I use ubuntu edgy...

---

