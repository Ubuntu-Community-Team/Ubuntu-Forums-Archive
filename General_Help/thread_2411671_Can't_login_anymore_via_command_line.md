---
title: "Can't login anymore via command line"
date: 2019-02-02
forum: General Help
---

### Post by gekomax on 2019-02-02
Hello, today my ubuntu based NAS doesn't allow me to login anymore. It's acting in a very strange way so made a 30 secs video to show you how exactly:

[https://youtu.be/tVe3qNo7t1M](https://youtu.be/tVe3qNo7t1M)

I changed keyboard and I can correctly login via recovery mode so I guess it's not an hardware issue.

 any suggestion?
Thanks a lot

---

### Post by TheFu on 2019-02-02
Can you ssh in?

Also, because the typing continues, constantly, we can't tell if it is a login prompt showing up over and over and over regardless of the input ... like the enter key is stuck?  Can't tell.

My Ubuntu "nas" has 4.4.0-141-generic (16.04) and isn't showing this issue.  I patched last night and rebooted immediately.  I did have to clean up some stale NFS handles by restarting the nfs-server, but it had been a month since that machine was rebooted.  I haven't tried to login on a console. Generally, I use ssh for all management.

---

### Post by konstantinos4 on 2019-02-02
I have exactly the same problem either in normal or recovery mode. :(
I managed however normally login using kernel 4.15.0-43
> **gekomax said:**
> Hello, today my ubuntu based NAS doesn't allow me to login anymore. It's acting in a very strange way so made a 30 secs video to show you how exactly:

[https://youtu.be/tVe3qNo7t1M](https://youtu.be/tVe3qNo7t1M)

I changed keyboard and I can correctly login via recovery mode so I guess it's not an hardware issue.

 any suggestion?
Thanks a lot

---

### Post by gekomax on 2019-02-03
> **TheFu said:**
> Can you ssh in? 

Sorry, I don't know. I've never used ssh.

> **TheFu said:**
> 
Also, because the typing continues, constantly, we can't tell if it is a login prompt showing up over and over and over regardless of the input ... like the enter key is stuck?  Can't tell.


Yes, that's correct. It's like the enter key is stuck but not permanently but it allow me to type something ramdomly (like in the video) o the correct password.


> **konstantinos4 said:**
> I have exactly the same problem either in normal or recovery mode. :(
I managed however normally login using kernel 4.15.0-43

Sorry, I don't understand if you found some fix. Did you fix it?

Thanks a lot ):P

---

