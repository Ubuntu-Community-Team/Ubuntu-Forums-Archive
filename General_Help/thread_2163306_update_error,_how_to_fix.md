---
title: "update error, how to fix?"
date: 2013-07-17
forum: General Help
---

### Post by gychang on 2013-07-17
on 12.04LTS, when I update I get this error:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

how do I fix this?

---

### Post by Bashing-om on 2013-07-17
gychang; Hi !
Make the authorization like so;
Terminal command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
```

That should make the system happy.

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by gychang on 2013-07-18
cured the problem, but what was wrong and what did the command do?

thanks,

> **Bashing-om said:**
> gychang; Hi !
Make the authorization like so;
Terminal command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
```

That should make the system happy.

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-18
gychang; Morning.

Hey, nothing was wrong ! Just ununtu's security measures in force. The command gave the system your acknowledgement that any files downloaded from
 "http://extras.ubuntu.com" is acceptable as a trusted site; which it is ... all files are verified as compatible with your version and no mal-ware is contained.
The same can not be said for other 3rd party sources. You must make that determination in that event and choose to also download and install their "keys"
for the system to accept that software. You are then stepping out from underneath ubuntu's umbrella of protection, and you are expected to know what you are doing.
Just one of the reasons that linux is considered a "secure" system.

If you are satisfied with this solution;
Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by gychang on 2013-07-18
thanks, now works well.

---

