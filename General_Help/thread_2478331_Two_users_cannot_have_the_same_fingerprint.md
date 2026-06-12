---
title: "Two users cannot have the same fingerprint"
date: 2022-08-23
forum: General Help
---

### Post by XargonWan on 2022-08-23
In my laptop I am using two different users for different purposes and I wish to enroll the same fingerprint to both of the users as I am phisically the same person.
However whenever I try to enroll a fingerprint already enrolled to another user I got this output:

```

fprintd-enrollUsing device /net/reactivated/Fprint/Device/0
Enrolling right-index-finger finger.
Enroll result: enroll-duplicate

```

How can I force the enroll of the same fingerprtin for both of the users?

---

### Post by TheFu on 2022-08-23
Use a different finger?

But fingerprints are known NOT to be secure, so if you seek real security, don't use them.
[https://www.nytimes.com/2017/04/10/technology/fingerprint-security-smartphones-apple-google-samsung.html](https://www.nytimes.com/2017/04/10/technology/fingerprint-security-smartphones-apple-google-samsung.html)
[https://www.csoonline.com/article/3330695/6-reasons-biometrics-are-bad-authenticators-and-1-acceptable-use.html](https://www.csoonline.com/article/3330695/6-reasons-biometrics-are-bad-authenticators-and-1-acceptable-use.html)

---

### Post by XargonWan on 2022-08-25
The point is that I wish to use the same finger

---

### Post by dragonfly41 on 2022-08-25
I started a biometrics venture (not fingerprint recognition) back in the 1980's and I know one issue. They all exhibit type 1 and type 2 errors (false acceptance rate and false rejection rate).

If you must use fingerprint recognition as your first line of defence then perhaps consider building as next layer, a Two Factor Authentication script so that two items are required to branch into different accounts.

But remember back doors such as LiveUSB.

---

### Post by miguel001 on 2022-08-25
Grab a finger from a little green alien from outer space as they work better or...

Its obviously because its sharing the same space with both users. You might be able to find a way to get it to have separate space or to separate it somehow.

If you can get another thing to help use the same one though its difficult to say but that's the other way. Maybe the following can help [https://www.systutorials.com/docs/linux/man/8-pam_fprintd/](https://www.systutorials.com/docs/linux/man/8-pam_fprintd/) and then use pam for all users or whatever.

Definitely a fprintd thing. I don't have a fingerprint reader so not looking into it further. But the two things I mention above should get the ball rolling.

---

