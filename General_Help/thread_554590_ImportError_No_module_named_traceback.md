---
title: "ImportError: No module named traceback"
date: 2007-09-19
forum: General Help
---

### Post by cancaseiro on 2007-09-19
I am trying to record movements on webpage for Funkload but get this error:

root@ubuntu:/home/villem# fl-record basic_navigation
Hit Ctrl-C to stop recording.
HTTP proxy listening on :8090
Recording to directory /tmp/tmpPrLAiR_funkload.
Traceback (most recent call last):
  File "/usr/bin/tcpwatch.py", line 1491, in <module>
    main(sys.argv[1:])
  File "/usr/bin/tcpwatch.py", line 1482, in main
    asyncore.loop(timeout=1.0)
  File "/usr/lib/python2.5/asyncore.py", line 191, in loop
    poll_fun(timeout, map)
  File "/usr/lib/python2.5/asyncore.py", line 132, in poll
    read(obj)
  File "/usr/lib/python2.5/asyncore.py", line 72, in read
    obj.handle_error()
  File "/usr/bin/tcpwatch.py", line 1266, in handle_error
    import traceback
ImportError: No module named traceback
Sorry no action recorded.

But this traceback does exist. It lies there /usr/lib/python2.5/traceback.py. Any suggestions what should I do to get it work properly?  I have messed with that problem very long time and I don't have any clues what to do :confused:

---

