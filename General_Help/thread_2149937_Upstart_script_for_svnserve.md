---
title: "Upstart script for svnserve?"
date: 2013-05-30
forum: General Help
---

### Post by GreatBunzinni on 2013-05-30
Does anyone happen to know what's the best way to use Upstart to get svnserve up and running?

I've managed to write the following script:
```

# svnserve - subversion server

description     "Subversion server to the local repository"

start on startup
stop on runlevel [016]

pre-start script
end script

script
        /usr/bin/svnserve -d --listen-port 424 -r "/media/DATA/subversion repo"
end script

post-start script
end script


```

This appears to work when calling sudo service svnserve start, but stopping the service simply hangs.

---

### Post by GreatBunzinni on 2013-06-28
Does anyone ever set a svnserve server with Ubuntu?

---

