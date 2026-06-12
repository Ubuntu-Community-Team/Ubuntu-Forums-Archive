---
title: "chmod follow symlinks"
date: 2015-08-09
forum: General Help
---

### Post by wolfgentleman on 2015-08-09
Same question as this, but thread was closed...
> **shkkmo said:**
> 
Is there anyway to modify file permissions in a way that traverses symlinks?

I see from reading docs from BSD and other operating systems that there is commonly a flag (-H or -L) that can be thrown on chmod to do this. However, not flag to do this appears to to available for the chmod command in ubuntu 12.04. Is there anyway to do this, is there a work around or another utility I can download? My google-fu is failing.

Here what I think would work in BSD for example:
chmod 755 -RLc /var/www/vhost/domain.tld/current/web

This should change the mode of the web folder, traverse it's tree and also follow symlinks in the web folder to change permissions in the linked plugin resources.


There must be some way to do this in Ubuntu, Right?

and the answer...
> **llamabr said:**
> 
You can get a little fancy:

[http://damonparker.org/blog/2007/06/27/recursive-chmod-tricks/](http://damonparker.org/blog/2007/06/27/recursive-chmod-tricks/)

is a dead link.

---

### Post by wolfgentleman on 2015-08-09
I think I found [a solution]("http://omasse.blogspot.com/2009/12/performing-chmod-on-symbolic-link.html"). I modified it to use chmod instead of umask and exit instead of return:
```

#!/bin/sh
if [ "${1}" = "" -o "${2}" = "" ]
then
       echo "Usage: lchmod  "
       exit 1
fi
umask=${1}
symlink=${2}


if [ ! -h ${symlink} ]
then
       echo "Symlink '${symlink}' does not exist"
       return 1
fi
destination=$(/bin/ls -l ${symlink} | sed 's/.*-> //g')
chmod ${umask} ${destination}
rm ${symlink}
ln -s ${destination} ${symlink}

```

I'm going to try it and edit the post to reflect the status.

[B]UPDATE:
[/B]It failed, I tried using umask as it was done in the OP, but it failed too.

---

