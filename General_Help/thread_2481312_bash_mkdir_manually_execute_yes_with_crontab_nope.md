---
title: "bash mkdir manually execute yes with crontab nope?"
date: 2022-11-25
forum: General Help
---

### Post by untidy4732 on 2022-11-25
Hey...

I'm making a backup script
When I'm executing the script "./g.sh" in terminal everything works fine.
But the script cant create a folder when executed with crontab?

```

tag=$(date "+%d")"_dc"
FILE="/home/myuser/dcbackup/"$tag.tar
ORDNER="/home/myuser/dcbackup/"$tag
TIMEST=$(date "+%s")


sudo mkdir -p $tag


cp /etc/crontab $ORDNER"/crontab"
#...much more

tar cvzf $FILE $ORDNER

```

Crontab
```
30 3 * * * root bash /home/myuser/dcbackup/g.sh

```

ls -li

```

 -rwxrwx--- 1 root      root 1125 Nov 25 11:54 g.sh

```

Do you have any idea? Thanks

---

### Post by untidy4732 on 2022-11-25
the problem was, that I wasn't using an absolute path to create the folder!

---

### Post by ActionParsnip on 2022-11-25
Always use full paths in everything you use in cron and in crontabs themselves. Saves issues.

---

### Post by Impavidus on 2022-11-26
There are a few other (potential) issues with your script.

Not only the absolute path to the backup directory wasn't supplied, but the absolute paths to the various tools you use were absent too. So you relied on a proper setting of the PATH environment variable. I can't tell you the default in Ubuntu right away, but in general, you can't count on PATH to be set properly when running something from crontab. Or any other environment variable, really.

The backup script is executed as root and owned by root, but it is in myuser's home directory. So now you have a file in myuser's home directory that myuser cannot edit. Not best practice. However, assuming that myuser owns the directory dcbackup or has write access to it, myuser can delete g.sh and replace it with a new g.sh, so that myuser can execute arbitrary code as root. That's certainly not best practice. The best place to put such home-made scripts that are normally executed by root is /usr/local/sbin.

If you already run the script as root, there's no need for sudo to elevate privileges to root.

---

### Post by untidy4732 on 2022-11-27
Thank you for your feedback! I'll edit it right now :)

---

