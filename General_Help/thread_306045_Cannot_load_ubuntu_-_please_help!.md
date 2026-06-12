---
title: "Cannot load ubuntu - please help!"
date: 2006-11-24
forum: General Help
---

### Post by natureboy316 on 2006-11-24
Hi,

I am using the dapper drake distro and have just come across the "your session has only lasted less than 10 seconds..." error msg.

The problem mentions the libkrb5.so.3 file; i have checked for this file in usr/lib and cannot find it.

Can sum1 plz help me out here as I'm pretty stumped as to how to fix this error?!

Thanks!

---

### Post by ReaderRat on 2006-11-24
It would be helpful if you could post the error message you got....

---

### Post by natureboy316 on 2006-11-24
Here are the full details:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem".

The details (~/.xsession-errors.file) give me this:

/usr/bin/ssh-agent: error while loading shared libraries: libkrb5.so.3: cannot open shared object file: No such file or directory

I can load the failsafe terminal version but everything else comes up with the above, apart from the failsafe GUI, which just crashes while loading.

---

### Post by ReaderRat on 2006-11-24
When I get a "no such file or directory" error, it is usually because I am in the wrong directory, or I failed to use "sudo" when I should have. That's about all I got on this....

---

