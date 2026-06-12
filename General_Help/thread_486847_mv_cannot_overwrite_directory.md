---
title: "mv: cannot overwrite directory"
date: 2007-06-28
forum: General Help
---

### Post by Jamie Jackson on 2007-06-28
From the CLI, I'm trying to move a directory's contents from one place to another. For whatever reason, my first move attempt only partially completed.

Now, I'm getting this, and I don't know how to recover from it in the CLI:

```

[user@machine jamieTemp]$ mv /var/www/thing/* thing/trunk/app/wwwroot/
mv: cannot overwrite directory `thing/trunk/app/wwwroot/events'
mv: cannot overwrite directory `thing/trunk/app/wwwroot/images'
mv: cannot overwrite directory `thing/trunk/app/wwwroot/research'

```

Where do I go from here?

Thanks,
Jamie

---

### Post by bodhi.zazen on 2007-06-28
You can ust the -f flag :

mv -f ....

This will overwrite files so be careful :)

---

### Post by Jamie Jackson on 2007-06-28
Unfortunately, I get precisely the same result with the -f flag.

---

### Post by bodhi.zazen on 2007-06-28
Depending on permissions you may need to sudo

sudo mv -f ....

---

### Post by Jamie Jackson on 2007-06-28
Thanks for sticking with the thread.

However, I just tried *as* root, and am still getting the same results.

```

[me@machine jamieTemp]$ su root
Password: 
[root@machine jamieTemp]# mv -f /var/www/thing/* thing/trunk/app/wwwroot/
mv: cannot overwrite directory `thing/trunk/app/wwwroot/events'
mv: cannot overwrite directory `thing/trunk/app/wwwroot/images'
mv: cannot overwrite directory `thing/trunk/app/wwwroot/research'

```

Thanks,
Jamie

---

### Post by bodhi.zazen on 2007-06-28
It seems GNU mv will not overwrite directories (mv will overwrite files) ...

So you will need to :

1. Deleter the existing directories in <destination> then mv <source> <destination>

or 

2. Do it in two steps copy then remove :

cp -rf .... <source> <destination>
rm -rf .... <source>

---

### Post by Jamie Jackson on 2007-06-28
Yeah, I think we're on the right track. However, -f doesn't seem to prevent overwrite prompting. So, it looks like I'd have to hit "y <enter>" thousands of times.

I'm looking through the cp man page:

```

       -i, --interactive
              prompt before overwrite

```

I need to do the opposite of -i, I need it to just blow right through and overwrite without my consent. I would have thought that the fact that cp has an -i flag would suggest that the default behavior is *not* to prompt, but I guess not.

Are you sure I've even got the syntax right of my command, by the way?
```
mv /var/www/thing/* thing/trunk/app/wwwroot/
```

Now that I've got the wwwroot directory at the destination, is there some way I can just move the directory, instead of its contents? Something like the following (I'm not sure about the syntax.)
```
mv /var/www/thing/ thing/trunk/app/wwwroot/
```

---

### Post by bodhi.zazen on 2007-06-28
LOL

use yes

```
yes | mv ....
```

Yes automatically pipes "y" to all those questions.

You can also override the -i flag ...

So, if mv has been aliased to mv -i 

To over ride this behavior use single quotes : ```
'mv' ....
```

or use unalias : ```
unalias mv
```

If you use unalias it will revert the next time you open a terminal

YOu need to edit ~/.bashrc if you want to change the default behavior ;)

---

### Post by Jamie Jackson on 2007-06-29
That last reply was really enlightening, thanks!

I had no idea about those existing aliases for cp, rm, and mv.(I'm SSHed into Redhat, but these aliases aren't on my Ubuntu system.)

Also, good to know about the piping of "yes"

I'm all set, with:
```
'cp' -rf src dest
```

Thanks again!
Jamie

---

