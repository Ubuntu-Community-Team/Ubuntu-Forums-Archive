---
title: "SSL error when running apt-add-repository"
date: 2015-09-01
forum: General Help
---

### Post by Notrev on 2015-09-01
Hi all,

I was using Kubuntu 14.10 and Firefox Developer Edition from *ubuntu-mozilla-daily/firefox-aurora* ppa repository.
I upgraded to Kubuntu 15.05 and the ppa repositories were commented out during the process, one of them was the firefox-aurora repository.

I have recently ran an *apt-get upgrade* and tried to add the firefox-aurora repository again, with the *apt-add-repository* command, but I'm getting an SSL error.

I tried reinstalling the ca-certificates package, but it did not fix.

Anyone has any clue about this?

Command output:
```

root@moria:~ # apt-add-repository ppa:ubuntu-mozilla-daily/firefox-aurora
Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1182, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1088, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1126, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1084, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 922, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 857, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1231, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.4/ssl.py", line 365, in wrap_socket
    _context=self)
  File "/usr/lib/python3.4/ssl.py", line 583, in __init__
    self.do_handshake()
  File "/usr/lib/python3.4/ssl.py", line 810, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 161, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 463, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 481, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 441, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1225, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1184, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 321, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 91, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading https://launchpad.net/api/1.0/~ubuntu-mozilla-daily/+archive/ubuntu/firefox-aurora: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1182, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1088, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1126, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1084, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 922, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 857, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1231, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.4/ssl.py", line 365, in wrap_socket
    _context=self)
  File "/usr/lib/python3.4/ssl.py", line 583, in __init__
    self.do_handshake()
  File "/usr/lib/python3.4/ssl.py", line 810, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 161, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 463, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 481, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 441, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1225, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1184, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 119, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 837, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 382, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 346, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 333, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 292, in _get_suggested_ppa_message
    lp_user = get_info_from_lp(LAUNCHPAD_USER_API % user)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading https://launchpad.net/api/1.0/~ubuntu-mozilla-daily: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)'

```

Thanks in advance.

---

### Post by monkeybrain20122 on 2015-09-01
"add-apt-respository"

and is there any reason why you login as root instead of using sudo?

---

### Post by Notrev on 2015-09-01
@monkeybrain20122

I use *sudo -s* to become root, because if I use *sudo <command>*, some environment variables I have set are not available.

Same error:
```

root@moria:~ # add-apt-repository ppa:ubuntu-mozilla-daily/firefox-aurora
Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1182, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1088, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1126, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1084, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 922, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 857, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1231, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.4/ssl.py", line 365, in wrap_socket
    _context=self)
  File "/usr/lib/python3.4/ssl.py", line 583, in __init__
    self.do_handshake()
  File "/usr/lib/python3.4/ssl.py", line 810, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 161, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 463, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 481, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 441, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1225, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1184, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 321, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 91, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading https://launchpad.net/api/1.0/~ubuntu-mozilla-daily/+archive/ubuntu/firefox-aurora: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1182, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1088, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1126, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1084, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 922, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 857, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1231, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.4/ssl.py", line 365, in wrap_socket
    _context=self)
  File "/usr/lib/python3.4/ssl.py", line 583, in __init__
    self.do_handshake()
  File "/usr/lib/python3.4/ssl.py", line 810, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 161, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 463, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 481, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 441, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1225, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1184, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 119, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 837, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 382, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 346, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 333, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 292, in _get_suggested_ppa_message
    lp_user = get_info_from_lp(LAUNCHPAD_USER_API % user)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading https://launchpad.net/api/1.0/~ubuntu-mozilla-daily: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:600)'

```

---

