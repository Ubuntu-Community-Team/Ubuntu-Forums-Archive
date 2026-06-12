---
title: "Cannot stop bluetoothd daemon"
date: 2014-06-06
forum: General Help
---

### Post by syntaxerror74 on 2014-06-06
Well, it looks like it.

Shutting down the daemon manually OUGHT to work like this:

```
sudo /etc/init.d/bluetooth stop
```

but it doesn't.
I am puzzled. /usr/sbin/bluetoothd doesn't respond to the script's 'stop' command at all, since it will still be found in your process list (ps -ef | grep blue). But why?

Oddly enough, you can use the script with the 'stop' command a hundred times! This is actually how I learned about the issue: I wanted to test if the script will actually complain if bluetoothd is NOT running and you try the stop option.

```
kill -9 <PID>
```

This worked, but doing this spawned a new bluetoothd with a new PID.

What am I doing wrong?

---

