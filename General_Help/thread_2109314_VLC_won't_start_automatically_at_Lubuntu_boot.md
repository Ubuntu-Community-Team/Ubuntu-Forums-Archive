---
title: "VLC won't start automatically at Lubuntu boot"
date: 2013-01-27
forum: General Help
---

### Post by mimac on 2013-01-27
Hello,

I am trying to configure VLC to start streaming two streams automatically on boot with Upstart.
Here is my upstart script stored in /etc/init/stream.conf:
  ```

description "VLC streams" 
start on (local-filesystems and net-device-up IFACE!=lo) 
stop on runlevel [016] 
exec /home/streamer/stream.sh
```and stream.sh:
  ```

#!/bin/bash
cvlc -v "/home/streamer/Videos/first/first.xspf" --sout '#std{access=udp{ttl=2},mux=ts,dst=239.220.220.31:9200}' --sout-keep --loop & 
cvlc -v "/home/streamer/Videos/second/second.xspf" --sout '#std{access=udp{ttl=2},mux=ts,dst=239.220.220.2:9200}' --sout-keep --random &
exit 0

```However, after the computer boots, there is no stream and VLC process  is not running. When I run stream.sh manually, it works with no  problem.

Does anybody know what mistake am I doing? Should I register upstart script somewhere?

  I am using Lubuntu 12.10 and VLC 2.0.5.

  Thank you in advance for any help.
  Milan

---

### Post by crtlbreak on 2013-07-07
hi Mimac - I know its been six months since your posting but wondered whether you had come right yet?

Just checking that the interface you are intending to use in your /etc/init/streams.conf is lo and not eth0?
and your user is called /home/streamer? where you put the stream.sh file?

Regards

---

