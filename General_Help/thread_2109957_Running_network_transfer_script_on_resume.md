---
title: "Running network transfer script on resume"
date: 2013-01-28
forum: General Help
---

### Post by irishetalon007 on 2013-01-28
Hello!

I'm trying to send files over ftp every time the computer starts or resumes. So far I got the start part correct by adding lines to /etc/rc.local, but the resume script is giving me trouble, and I don't know why. Here's the resume script, /etc/pm/sleep.d/99_ftp_files:

```
#!/bin/bash

# takes a picture from webcam and sends it to ftp

case "$1" in
    	thaw|resume)
		sleep 10
		wput my_file ftp://myftp
		;;
	*)
		;;
esac
```

However, for some reason this script causes my network to become disabled and I can't recover from it, even after unloading and reloading network drivers.

What about my script causes the network to remain down after resume?

---

