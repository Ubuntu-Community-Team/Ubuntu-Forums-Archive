---
title: "Start YouTube video from terminal and exit once done?"
date: 2013-01-21
forum: General Help
---

### Post by Kdar on 2013-01-21
How can I start YouTube video from terminal and exit once its done?

I am trying to run some performance tests on Ubuntu and I am trying to think of a way to play single instance of YouTube (flash) video this way..... Can anyone give me some idea on how its possible to do?

I can for example open firefox with line, but how can I exist command once video is stopped playing?

---

### Post by |{urse on 2013-01-21
Create a bash script named youtube (or whatever) containing the following in your home directory.


#!/bin/bash
/usr/bin/firefox -new-window [http://www.youtube.com/watch?v=NzdUy90vTuk](http://www.youtube.com/watch?v=NzdUy90vTuk) &
sleep 5s
kill -HUP $(pgrep -x firefox)
echo "all done!"


MAke it executable

> chmod +x youtube

launch it with ./youtube

Change the 5s to 5m for 5 minutes of test, for example.

---

### Post by Kdar on 2013-01-21
And why do you have sleep 5m there?

---

### Post by |{urse on 2013-01-21
To set it to sleep for 5 minutes, I'd say whatever length your youtube vid is add 5 seconds to that time.

---

### Post by Kdar on 2013-01-21
Ah I get it now... I failed to notice " &" in your 2nd line of script.
Now this makes sense. Thank you.

---

### Post by |{urse on 2013-01-22
Not a problem ;)

---

### Post by andrew.46 on 2013-01-23
Perhaps a little simpler:

```

cvlc --play-and-exit 'http://www.youtube.com/watch?v=NzdUy90vTuk'

```

---

### Post by |{urse on 2013-01-23
Nice! How bout that?

---

