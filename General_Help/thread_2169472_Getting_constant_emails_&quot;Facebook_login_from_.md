---
title: "Getting constant emails &quot;Facebook login from Facebook Chat&quot;"
date: 2013-08-22
forum: General Help
---

### Post by lunatico on 2013-08-22
Hi All,

Posting this question here because I really don't know where's the best place to ask this, and there's a good chance that someone here will have an answer. Asking Facebook directly and getting an answer is close to impossible.

I have configured my Pidgin to connect to Facebook's chat using XMPP, as per their [instructions]("https://www.facebook.com/sitetour/chat.php").
It works fine, however, I getting email very frequently when my Pidgin connects or re-connects to Facebook Chat. Usually when I move from wire to wireless connection. The emails are very generic and unhelpful, they usually go like this:
[SIZE=2][I]It looks like someone logged into "Facebook Chat" on Thursday, 22 August 2013 at 09:04.
If this was you, please disregard this email.
If this wasn't you, please secure your account, as someone else may be accessing it.
Thanks,
The Facebook Security Team[/I][/SIZE]

No source IP, no XMPP resource name.... nothing. The first time I got worried, so I changed my passwords and the whole lot... I then changed the password a second time but then realized it wasn't that someone else was using it, it was my Pidgin re-connecting.

Is anyone else getting this?
Does anyone know why this is happening?
Does anyone know how to avoid this?

Thanks very much.

---

### Post by pilgrim689 on 2013-08-25
Yes. I am getting this as well with Empathy. One workaround is to go to Facebook and under Settings->Security Settings->Login Notifications, uncheck "Email".

Note, however, that you then lose the feature where if a malicious user logs into your account from a new device, you will not get notified...

---

### Post by vleonbonnet2 on 2013-09-13
I am getting the same emails, however I don't want to remove the notifications in case my account gets hijacked. For now, I think the best is to create a mail rule that filters this email only if it says 'Facebook Chat'.

---

