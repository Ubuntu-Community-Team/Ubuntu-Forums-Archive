---
title: "missing ldap.conf from /etc/"
date: 2016-02-01
forum: General Help
---

### Post by ozelera on 2016-02-01
Hi, I'm new here. Recently, at my work place we have encountered a problem where the file "ldap.conf" mysteriously missing from "/etc/" which make some users unable to log in. To solve this, we just copy "ldap.conf" from "/etc/ldap/ldap.conf" to "/etc/".

However, after some time the file keeps disappearing. I was wondering if you know what the cause of the disappearing file and how to solve this.

Thank you.

Best regards,

---

### Post by Irihapeti on 2016-02-02
*Thread moved to **General Help**.*

---

### Post by ozelera on 2016-02-03
Thank you for moving the thread. Hopefully, someone can help me with this issue.

---

### Post by matt_symes on 2016-02-03
Hi

Is it disappearing right after an update ? 

Is there some package conflict that's removing the file ?

Kind regards

---

### Post by ozelera on 2016-02-05
Hello,

thank you for asking.

There is no update involve, the file just gone missing randomly.

I am not sure whether there is any package conflict because the file was able to stay there for quite sometime before it went missing.

We have been having this problem for quite sometime but we were not able to find out what actually causing the missing file.

thank you. best regards :)

---

### Post by matt_symes on 2016-02-05
Hi

No update ? That's odd.

Some thoughts. 

You could make the file immutable but that may cause you problems when ldap is updated.

```
sudo chattr +i /etc/ldap/ldap.conf
```

I think what i would personally look into is the package auditd. Try to work out which process and user is deleting the file (as something obviously is).

```
sudo apt-get install auditd
```

Set up a syscall watch along the lines of (this is an example only)

```
sudo auditctl -a exit,always -Farch=b64 -S unlink -S unlinkat -k "file-deleted"
```

Change arch=b64 to arch=b32 if you are using 32bit, or add both rules for a mixed environment.

This will log *all* deleted files.

After the file has been deleted, use ausearch to find out what happened to that file (someting along the lines of..).

```
sudo ausearch -k file-deleted -f ldap.conf
```

You'll need to do some reading up on auditd as it's pretty powerful, has many options and i may have got the instructions above wrong. It's been ages since i looked into auditd so please make sure you read up yourself.

Please post back on how you get on.

Kind regards

---

### Post by ozelera on 2016-02-08
Thank you very much. I will check with your instruction.

---

### Post by ozelera on 2016-03-28
Hello,

So after installing auditd, the ldap.conf never went missing. However, the content of the ldap.conf file were seen to be modified without any records of modification.

This is really weird, This happens only to a set of Laptops (Dell Latitude 3330). We have other another set (Dell Latitude 3340) which never had such problem, could it be problem with hardware?

---

### Post by ozelera on 2016-04-07
I have given up, it's probably because of the laptops model.

We decided to use "rsync -az /etc/ldap/ldap.conf /etc/" in one of our startup files so that every time the computers start, the file is automatically copied into the folder. 

Thank you very much for giving us option. :)

---

