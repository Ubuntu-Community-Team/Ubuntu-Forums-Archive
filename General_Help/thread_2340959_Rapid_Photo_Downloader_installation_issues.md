---
title: "Rapid Photo Downloader installation issues"
date: 2016-10-23
forum: General Help
---

### Post by mbria2 on 2016-10-23
Hi all,

I'm a proud user of RPD. It's, by far, the best software I ever found to download your pictures from your cams.

The point is that the old version started to fail (bad renaming unpairing JPG/NEF become a mess) so I accept it's time to move.

I'm a ubuntu 15.10 (I will probably move to Xenial soon) so I follow the installation instructions published here:
[http://www.damonlynch.net/rapid/download.html](http://www.damonlynch.net/rapid/download.html)

The install runs without any trouble, but when I run the application I got this error:

```
$ rapid-photo-downloader 
ERROR    An unhandled exception occurred
ERROR    An unhandled exception occurred
ERROR    An unhandled exception occurred
ERROR    Traceback (most recent call last):
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/interprocess.py", line 1009, in startReceiver
    socks = dict(poller.poll())
  File "/usr/lib/python3/dist-packages/zmq/sugar/poll.py", line 101, in poll
    return zmq_poll(self.sockets, timeout=timeout)
  File "zmq/backend/cython/_poll.pyx", line 115, in zmq.backend.cython._poll.zmq_poll (zmq/backend/cython/_poll.c:1613)
  File "zmq/backend/cython/checkrc.pxd", line 21, in zmq.backend.cython.checkrc._check_rc (zmq/backend/cython/_poll.c:2043)
zmq.error.ZMQError: Llamada al sistema interrumpida


ERROR    Traceback (most recent call last):
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/interprocess.py", line 241, in run_sink
    worker_id, directive, content = self.receiver_socket.recv_multipart()
  File "/usr/lib/python3/dist-packages/zmq/sugar/socket.py", line 300, in recv_multipart
    parts = [self.recv(flags, copy=copy, track=track)]
  File "zmq/backend/cython/socket.pyx", line 631, in zmq.backend.cython.socket.Socket.recv (zmq/backend/cython/socket.c:5799)
  File "zmq/backend/cython/socket.pyx", line 665, in zmq.backend.cython.socket.Socket.recv (zmq/backend/cython/socket.c:5599)
  File "zmq/backend/cython/socket.pyx", line 139, in zmq.backend.cython.socket._recv_copy (zmq/backend/cython/socket.c:1752)
  File "zmq/backend/cython/checkrc.pxd", line 21, in zmq.backend.cython.checkrc._check_rc (zmq/backend/cython/socket.c:6275)
zmq.error.ZMQError: Llamada al sistema interrumpida


ERROR    Traceback (most recent call last):
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/interprocess.py", line 241, in run_sink
    worker_id, directive, content = self.receiver_socket.recv_multipart()
  File "/usr/lib/python3/dist-packages/zmq/sugar/socket.py", line 300, in recv_multipart
    parts = [self.recv(flags, copy=copy, track=track)]
  File "zmq/backend/cython/socket.pyx", line 631, in zmq.backend.cython.socket.Socket.recv (zmq/backend/cython/socket.c:5799)
  File "zmq/backend/cython/socket.pyx", line 665, in zmq.backend.cython.socket.Socket.recv (zmq/backend/cython/socket.c:5599)
  File "zmq/backend/cython/socket.pyx", line 139, in zmq.backend.cython.socket._recv_copy (zmq/backend/cython/socket.c:1752)
  File "zmq/backend/cython/checkrc.pxd", line 21, in zmq.backend.cython.checkrc._check_rc (zmq/backend/cython/socket.c:6275)
zmq.error.ZMQError: Llamada al sistema interrumpida


QObject::connect: Cannot queue arguments of type 'QTextBlock'
(Make sure 'QTextBlock' is registered using qRegisterMetaType().)
Fatal Python error: Segmentation fault


Thread 0x00007f2973de7700 (most recent call first):


Thread 0x00007f29735e6700 (most recent call first):


Thread 0x00007f2972de5700 (most recent call first):


Thread 0x00007f29725e4700 (most recent call first):


Thread 0x00007f2994846700 (most recent call first):
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/excepthook.py", line 96 in excepthook


Current thread 0x00007f29cac80700 (most recent call first):
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/rapid.py", line 1063 in showMainWindow
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/rapid.py", line 1054 in initStage3
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/thumbnailer.py", line 187 in loadBalancerFrontendPort
  File "/home/turing/.local/lib/python3.4/site-packages/raphodo/rapid.py", line 5183 in main
  File "/home/turing/bin/rapid-photo-downloader", line 11 in <module>
Violación de segmento (`core' generado)

```
I tried it with my default python version (3.4.3+) and also with 3.5 (that crashes in the install script). 

I googled, but I found nothing about this.

Any suggestion about how to deal with this?

Thanks for your help,
m.

---

### Post by mbria2 on 2016-10-23
Posted in launchpad as the developer requests in his webpage:
[https://bugs.launchpad.net/rapid/+bug/1636026](https://bugs.launchpad.net/rapid/+bug/1636026)

---

### Post by bearlake on 2016-10-23
15.10 has reached EOL sometime ago.

Best to install 16.04 before doing anything.

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

