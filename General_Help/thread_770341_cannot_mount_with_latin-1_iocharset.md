---
title: "cannot mount with latin-1 iocharset"
date: 2008-04-27
forum: General Help
---

### Post by Fibonacci on 2008-04-27
When trying to mount other partitions, either via fstab or the command line, the characters outside the ASCII range in the filenames appear as question marks. The reason for this appears to be that, while the filenames were encoded with latin-1 (iso8859-1), mount is reading them as utf8, no matter which iocharset I have specified.
I've tried -o iocharset=iso8859-1, -o iso8859-1, -o iocharset=utf8, -o utf8, but the result is always the same: question marks instead of the expected characters. How can I force it to read filenames in another encoding?

Thanks in advance.

---

### Post by Fibonacci on 2008-04-27
Nevermind, it seems that the problem magically solved itself. I'm not doing anything different, and yet it's working now.

---

