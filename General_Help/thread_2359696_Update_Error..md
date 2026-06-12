---
title: "Update Error."
date: 2017-04-26
forum: General Help
---

### Post by poorguy on 2017-04-26
Hello,

I just installed xubuntu 16.04 32 bit and the install went great.
I did a sudo apt update && sudo apt upgrade and this error showed up "some metadata was ignored due to errors".

I found this and applied it.
[https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d](https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d)

This is my output after applying the above fix.

~$ appstreamcli --version
AppStream CLI tool version: 0.10.6

Is this all that is needed to be done for this bug.

Thanks

The PoorGuy

---

### Post by #&amp;thj^% on 2017-04-26
> **poorguy said:**
> Hello,

I just installed xubuntu 16.04 32 bit and the install went great.
I did a sudo apt update && sudo apt upgrade and this error showed up "some metadata was ignored due to errors".

I found this and applied it.
[https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d](https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d)

This is my output after applying the above fix.

~$ appstreamcli --version
AppStream CLI tool version: 0.10.6

Is this all that is needed to be done for this bug.

Thanks

The PoorGuy

As explained:
> The bug has been fixed in appstream package version 0.10.1,
and your using 0.10.6.....so if that was the same error that you also had....you now should be good to go!
And you can check again with:
```
sudo apt update
```
should now work as expected.

---

### Post by poorguy on 2017-04-26
Hey 1fallen,

Pretty much what I thought but wanted to make certain.
Everything I did in the "askUbuntu" page I found worked 100%.

Thanks for the reply. 

I'll mark this solved.

Thanks

The PoorGuy ;)

---

### Post by #&amp;thj^% on 2017-04-26
Cool...Glad to hear this is now flush again.:D
Cheers

---

### Post by poorguy on 2017-04-26
Of course since my iso of Xubuntu 16.04 was downloaded on the first day it was released I would get the iso with a bug.

That's what I get for wanting it the day it's released.

---

