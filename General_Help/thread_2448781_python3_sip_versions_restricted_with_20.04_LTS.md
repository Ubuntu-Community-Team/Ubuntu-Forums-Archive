---
title: "python3 sip versions restricted with 20.04 LTS"
date: 2020-08-13
forum: General Help
---

### Post by 0n0w1c on 2020-08-13
With 20.04 we have the package python3-sip_4.19.21+dfsg-1build1 and if you perform a $pip3 list you will indeed see sip==4.19.21 installed.
If I then make a venv virtual environment via $python3 -m venv testenv and perform a pip3 list, no sip is installed in the venv. So far, so good.
Now, perform a $pip3 install sip and check with $pip3 list you will see sip 5.3.0 installed.

If I attempt the same again but this time specify sip==4.19.21 I receive the following:
```

ERROR: Could not find a version that satisfies the requirement sip==4.19.21 (from versions: 5.0.0, 5.0.1, 5.1.0, 5.1.1, 5.1.2, 5.2.0, 5.3.0)
ERROR: No matching distribution found for sip==4.19.21

```

No versions before 5.0 can be installed via pip3. PyPi shows 4.19.8 as being available but it gives the same error.
Why do I seem to be locked into sip >= 5.0?

---

### Post by 0n0w1c on 2020-08-13
Installing sip==4.19.x from source into my venv works fine, so that will be my work-around.
I would still like to know what is forcing the 5.0 version of sip via pip.

---

### Post by 0n0w1c on 2020-08-13
Speculation...

It may be that the sip 4.19.x versions on PyPi are for Python <= 2.7
And that pip5 was intended for 3.8 so they stopped updating the 4.19.x sip versions that were for python 2.7 once it became deprecated. And so now pip3 only finds the sip 5.x versions available as they are the only ones on PyPi that are suitable.

---

