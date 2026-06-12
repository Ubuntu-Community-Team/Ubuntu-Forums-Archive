---
title: "Broken Package: python-poker2d"
date: 2007-06-03
forum: General Help
---

### Post by jrattner on 2007-06-03
The package python-poker2d does not work on my system.  It opens up draws the window, loads data then fails are returns me to the command line where I'm confronted with a mirage of errors.  Does anyone have any solution to this?

---

### Post by mystman on 2007-06-03
What's the error output?

---

### Post by jrattner on 2007-06-04
jrattner@jrattner-laptop:~$ poker2d 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/pokerclient2d/poker2d.py", line 149, in run
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 206, in callback
    log.callWithLogger(source, self._doReadOrWrite, source, condition)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger
    return callWithContext({"system": lp}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext
    return context.call({ILogContext: newCtx}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext
    return func(*args,**kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 203, in _doReadOrWrite
    self._disconnectSelectable(source, why, didRead == source.doRead)
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 255, in _disconnectSelectable
    selectable.connectionLost(f)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 576, in connectionLost
    Connection.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 416, in connectionLost
    protocol.connectionLost(reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1215, in connectionLost
    UGAMEClientProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 100, in connectionLost
    UGAMEProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/protocol.py", line 93, in connectionLost
    self.protocolInvalid("different", PROTOCOL_MAJOR + "." + PROTOCOL_MINOR)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1411, in protocolInvalid
    UGAMEClientProtocol.protocolInvalid(self, server, client)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 93, in protocolInvalid
    self.factory.established_deferred.errback((self, server, client),)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 261, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 290, in _startRunCallbacks
    raise AlreadyCalledError
twisted.internet.defer.AlreadyCalledError: 
jrattner@jrattner-laptop:~$

---

### Post by josh420 on 2007-06-04
I'm having the exact same problem. 

Any Ideas?

---

### Post by mystman on 2007-06-04
I'm guessing it's a problem with the package.  I'll try installing it to see...

Ok, same thing for me.  I guess the package is broke.  Maybe you could try finding the source somewhere online and compiling yourself?

---

### Post by jrattner on 2007-06-04
Where can I locate the source?

---

### Post by ramasdf123 on 2007-06-12
this is a proble with the network setup, which i a not sure how to set up yet

---

### Post by raucous1 on 2007-06-13
I am having pretty much the same error

If anyone figures this out let us know!

xyz@ite:~$ poker2d
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/pokerclient2d/poker2d.py", line 149, in run
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 206, in callback
    log.callWithLogger(source, self._doReadOrWrite, source, condition)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger
    return callWithContext({"system": lp}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext
    return context.call({ILogContext: newCtx}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext
    return func(*args,**kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 203, in _doReadOrWrite
    self._disconnectSelectable(source, why, didRead == source.doRead)
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 255, in _disconnectSelectable
    selectable.connectionLost(f)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 576, in connectionLost
    Connection.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 416, in connectionLost
    protocol.connectionLost(reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1215, in connectionLost
    UGAMEClientProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 100, in connectionLost
    UGAMEProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/protocol.py", line 93, in connectionLost
    self.protocolInvalid("different", PROTOCOL_MAJOR + "." + PROTOCOL_MINOR)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1411, in protocolInvalid
    UGAMEClientProtocol.protocolInvalid(self, server, client)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 93, in protocolInvalid
    self.factory.established_deferred.errback((self, server, client),)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 261, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 290, in _startRunCallbacks
    raise AlreadyCalledError
twisted.internet.defer.AlreadyCalledError:

---

