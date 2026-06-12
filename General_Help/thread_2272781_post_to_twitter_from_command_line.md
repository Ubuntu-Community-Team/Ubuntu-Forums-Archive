---
title: "post to twitter from command line"
date: 2015-04-08
forum: General Help
---

### Post by sohlinux on 2015-04-08
Hello, How can I post to twiter from the command line? I have tried many ways but none will work. for example

#!/bin/bash
# tweet_mess.sh  Tweet from your Linux account

USERNAME"username"
PASSWORD="password"

URL=http://twitter.com/statuses/update.xml
# Post to Twitter.
result=`curl -u $USERNAME:$PASSWORD -d
status="This is where you will place your message for Twitter"
$URL`

exit 0

---

### Post by sohlinux on 2015-04-08
anyone :(

---

### Post by Habitual on 2015-04-08
> **sohlinux said:**
> ```
$URL`
```

That looks iffy all by itself and with an '`' in it also.
Where did this script originate?
Did it ever work?

Also use this under 
```
#!/bin/bash
set -x
...
```
and then run the script to display the variables.

---

### Post by Holger_Gehrke on 2015-04-09
Well, it is correct syntax, but could be written somewhat clearer by putting the output substitution on one line:
```

#!/bin/bash
# tweet_mess.sh  Tweet from your Linux account

USERNAME"username"
PASSWORD="password"

URL=http://twitter.com/statuses/update.xml
# Post to Twitter.
result=$( curl -u $USERNAME:$PASSWORD -d status="This is where you will place your message for Twitter" $URL )

exit 0
```

The question is of course whether or not the URL and the name of the POST-data field are still right. Twitter has been known to change these. The Twitter API - Documentation at [https://dev.twitter.com/rest/reference/post/statuses/update](https://dev.twitter.com/rest/reference/post/statuses/update)
gives "https://api.twitter.com/1.1/statuses/update.json" as the URL and says the data has to be URL-encoded, so it should be '--data-urlencode' instead of '-d'.

---

### Post by sohlinux on 2015-04-09
thanks guys, I played around with this for hours, it doesnt work, did you actually get it to work or is this theory? thanks

---

