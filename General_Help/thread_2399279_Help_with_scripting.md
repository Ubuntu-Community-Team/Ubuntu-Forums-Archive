---
title: "Help with scripting"
date: 2018-08-23
forum: General Help
---

### Post by raleigh3 on 2018-08-23
This isn't my code.

I need help understanding the format of REGEX. (It's Greek to me.)

I am willing to read up on it, but don't know where to look?

```
#!/bin/bash
TARGET_DIR='/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Script_Backups/'
REGEX='Ubuntu_Scripts_[0-9]{4}-[0-9]{2}-[0-9]{2}-[0-9]{2}-[0-9]{2}[.]zip'
LATEST_FILE="$(ls "$TARGET_DIR" | egrep "${REGEX}$" | tail -1)"

find "$TARGET_DIR" ! -name "$LATEST_FILE" -type f -regextype egrep -regex ".*/${REGEX}$" -exec rm -f {} +
```

---

### Post by &amp;KyT$0P# on 2018-08-23
Does [this tutorial]("http://www.zytrax.com/tech/web/regex.htm") help?

---

### Post by raleigh3 on 2018-08-23
Thanks. Great tutorial !!

---

### Post by &amp;KyT$0P# on 2018-08-23
You're welcome.

---

