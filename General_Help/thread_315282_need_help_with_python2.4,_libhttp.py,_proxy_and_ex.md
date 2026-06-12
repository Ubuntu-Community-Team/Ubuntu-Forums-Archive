---
title: "need help with python2.4, libhttp.py, proxy and exaile"
date: 2006-12-08
forum: General Help
---

### Post by kkellner on 2006-12-08
I have been trying to get exaile working properly on my edgy gnome setup.  The program seems to be working alright but none of the web-enabled activities (album art fetching, wikipedia, etc.) work.  I ran the program in the terminal and came up with many errors:

```
ken@brutus:~$ exaile
Introspect error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/share/exaile/xl/dbusinterface.py", line 208, in test
    iface.test_service("testing dbus service")
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Error grabbing key 162, 0x82eb018
Streamripper not found
mmkeys are available.
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/ken/.exaile/saved/playlist0000.m3u
new thread created with Catch 22 - Keasbey Nights
cover thread started
new thread created with Catch 22 - Keasbey Nights
cover thread started
Aborted cover thread
playing has been stopped on 'Keasbey Nights'
Traceback (most recent call last):
  File "/usr/share/exaile/xl/covers.py", line 107, in run
    conn.request("GET", string)
  File "httplib.py", line 804, in request
    self._send_request(method, url, body, headers)
  File "httplib.py", line 827, in _send_request
    self.endheaders()
  File "httplib.py", line 798, in endheaders
    self._send_output()
  File "httplib.py", line 679, in _send_output
    self.send(msg)
  File "httplib.py", line 646, in send
    self.connect()
  File "httplib.py", line 630, in connect
    raise socket.error, msg
error: (110, 'Connection timed out')

```
My limited knowledge suggests that the problem is somehow related to the internet proxy at my school somehow not working with httplib.py and proxy.py but I have no idea how to make this work.  Anyone able to help me with this?

---

### Post by DocHoliday52090 on 2007-06-10
I too have this error. 

Reinstalling Exaile doesn't seem to help, neither does using aptitude purge and installing it again.

Exaile also takes forever to load.

---

