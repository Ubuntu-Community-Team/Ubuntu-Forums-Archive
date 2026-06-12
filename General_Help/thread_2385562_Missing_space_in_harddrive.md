---
title: "Missing space in harddrive"
date: 2018-02-21
forum: General Help
---

### Post by Pandee on 2018-02-21
Hello,

The Image below shows my current /var setup. The setup is so i should have about 451GB in space in /var . The space it uses is correct and so is the total. But I am missing a large amount of space (as you can see I am 94% full however var only hows 103.7GB used.  Anyone have ideas on where my space has gone?
[ATTACH=CONFIG]278621[/ATTACH]

---

### Post by QIII on 2018-02-22
Hello!

Please use the attachment functionality provided by the paperclip icon above the text entry box to insert thumbnail images our users may click to view at their discretion.

Some users have slow connections, data limits, or work from mobile devices.  Please avoid inserting or linking large images for their sake.

Thanks.

---

### Post by Pandee on 2018-02-22
Ahh, Sorry. Fixed

---

### Post by deadflowr on 2018-02-22
Look at df as opposed to ncdu (or du) and the output of whatever any file manger might say.
```
df -h
```
I somehow remember once upon a time seeing people having issues with graphical file managers reading the wrong values, or incomplete values.

And du (or ncdu) only ever show the used value and not the total values.
So not really helpful to find full disk sizes.
Only actually good to see which files and directories space are currently used.
If that makes sense.

---

### Post by Pandee on 2018-02-22
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G  9.3G  8.9G  52% /
devtmpfs         63G  4.0K   63G   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none             13G  1.5M   13G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             63G  196K   63G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/md2        421G  381G   18G  96% /var

```

Is what i get, Whats the next step?

(Thanks deadflower)

---

### Post by deadflowr on 2018-02-22
Was ncdu run as sudo(root)?
I ask because some directories/files in /var might not be readable to non-root users.
So running it as a normal (non-root) user might not show all.

Also, I see it's /dev/md2 which I would assume means it's a raid array.
Not sure if that might be something.

---

### Post by Pandee on 2018-02-22
Hey deadflowr,

The command gave out the same output as before. No sign of that missing 300GB.

---

