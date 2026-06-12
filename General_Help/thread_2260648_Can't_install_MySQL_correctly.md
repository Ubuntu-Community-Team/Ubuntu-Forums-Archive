---
title: "Can't install MySQL correctly"
date: 2015-01-13
forum: General Help
---

### Post by DiogoSaraiva on 2015-01-13
I'm getting this error when I install mysql-server.

[Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.

What can I do?
I read a do various things already from other forums and didn't resolved...

Or can I ignore It...
I want to install Joomla...

Thank you very much and have a nice day...

---

### Post by sandyd on 2015-01-13
> **DiogoSaraiva said:**
> I'm getting this error when I install mysql-server.

[Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.

What can I do?
I read a do various things already from other forums and didn't resolved...

Or can I ignore It...
I want to install Joomla...

Thank you very much and have a nice day...

This is not an error - just a warning that key_buffer will be removed (depreciated) in a future release. It has not happened yet, so it is not really anything to worry about at the moment.

If you want to remove the warning, run
```

sudo sed -i s/key_buffer/key_buffer_size/g /etc/mysql/my.cnf
```

---

### Post by DiogoSaraiva on 2015-01-13
Ohh, 
so, sorry for the inconvenience, and thanks...

by the way I try to answer some questions in the forum but I can't/ don't know the answer almost all times, and I every day (almost) post a new thread, and I appreciate very much who answer me... but i can't reply the favour; I'm only 17 years old... Sorry for that...

could there be any problem?
you're forum moderator...
can you answer me this?


Thank you very much and have a nice day...

---

