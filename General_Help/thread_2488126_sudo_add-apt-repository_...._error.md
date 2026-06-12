---
title: "sudo add-apt-repository .... error"
date: 2023-06-23
forum: General Help
---

### Post by habernir on 2023-06-23
when i try to add  ppa in ubuntu 22.04
its write me 

```
Traceback (most recent call last):  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1363, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1139, in connect
    address_info = socket.getaddrinfo(host, port, 0, socket.SOCK_STREAM)
  File "/usr/lib/python3.10/socket.py", line 955, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 364, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 347, in main
    shortcut = handler(source, **shortcut_params)
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 40, in shortcut_handler
    return handler(shortcut, **kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 82, in __init__
    if self.lpppa.publish_debug_symbols:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 494, in login_anonymously
    return cls(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 230, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 477, in __init__
    self._browser.get(root_resource), 'application/json')
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 439, in get
    response, content = self._request(url, extra_headers=headers)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 389, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 359, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1725, in request
    (response, content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 144, in _request
    response, content = super(LaunchpadOAuthAwareHttp, self)._request(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 184, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1441, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1370, in _conn_request
    raise ServerNotFoundError("Unable to find the server at %s" % conn.host)
httplib2.error.ServerNotFoundError: Unable to find the server at api.launchpad.test
``` 


anyone know what the problem?

---

### Post by ian-weisser on 2023-06-23
Well, your output says:

> socket.gaierror: [Errno -2] Name or service not known

and

> httplib2.error.ServerNotFoundError: Unable to find the server at api.launchpad.test

And, of course, there is no such server as "launchpad.test"

---

### Post by habernir on 2023-06-24
do you know how can i fix that?

---

### Post by habernir on 2023-06-24
> **ian-weisser said:**
> Well, your output says:



and



And, of course, there is no such server as "launchpad.test"
Do you know how can i fix that?

---

### Post by habernir on 2023-06-24
solved by:

sudo rm -rf /root/.launchpadlib/api.launchpad.net/cache/

---

