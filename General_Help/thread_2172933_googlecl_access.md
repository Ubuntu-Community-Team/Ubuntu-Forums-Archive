---
title: "googlecl access"
date: 2013-09-07
forum: General Help
---

### Post by bill-lancaster on 2013-09-07
I've been using googlecl from the command line for some time.
Have just a new installation of 13.04 and can't get access to my google stuff.
For example:-
```
google calendar add "test2222"  --user wlancaster44
```
produces:-
```
Please log in and/or grant access via your browser at https://www.google.com/accounts/OAuthAut2FlZYgyvjgFyBRWT3ucdhbDPYKey07&hd=default then hit enter
```
I have been able to make entries to calendar from the command line but each time having to go through a registration process.
Can't figure out where I'm going wrong.

---

### Post by bill-lancaster on 2013-09-07
Found this in another post - the idea is that it would correct past faliures to register.
```
CQ2960EA:~$ google calendar list --user wlancaster44@gmail.com --force-auth
```

But stil get this response:-
```
Please log in and/or grant access via your browser at https://www.google.com/accounts/OAuthAuthorizeToken?oauth_token=4%2FGj6AlsFn43jm6eHNneYsaHuP50ZN&hd=default then hit enter.QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
unnamed app(4527) kdemain: rekonq is already running! 

```

Still no progress!

---

### Post by bill-lancaster on 2013-09-07
So far have been trying only calendar access so I tried to list contacts and got the login request from Google together with verification code.

Now I have full access to contacts.

Tried same with calendar and gained full access also

---

