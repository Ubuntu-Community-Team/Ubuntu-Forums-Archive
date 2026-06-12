---
title: "mail not accepting some switches"
date: 2017-08-15
forum: General Help
---

### Post by jjhudak on 2017-08-15
I recently installed mailutils under 16.04 lts server.
In addition, I installed ssmtp.  
From the command line I issue
```

echo "PC alive" | mail -s "PC Status" me@gmail.com

```

Everything is fine and the mail is sent and correctly received

I then try:
```

echo "PC alive" | mail -v -s "PC Status" me@gmail.com

```

and get the error:
```

mail: invalid option -- 'v'
Try 'mail --help' or 'mail --usage' for more information.

```


I then tried the -d switch, and the same thing happened.
according to ubuntu man pages, they are valid switches.
Can anyone explain why mail chokes on these switches???
Thanks
J

---

