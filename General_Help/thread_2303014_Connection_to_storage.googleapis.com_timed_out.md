---
title: "Connection to storage.googleapis.com timed out"
date: 2015-11-15
forum: General Help
---

### Post by AkiraBergman on 2015-11-15
I am trying to install Google tensorflow binary on ubuntu 15.10 and getting the following timeout. I searched for this on the web to no avail. I am not using network proxies. I got few things on the browser Chromium but that should not matter to my knowledge. I am in Turkey but this should not matter either.

akira@u1510:~$ pip install [https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.5.0-cp27-none-linux_x86_64.whl](https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.5.0-cp27-none-linux_x86_64.whl)
Downloading/unpacking [https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.5.0-cp27-none-linux_x86_64.whl](https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.5.0-cp27-none-linux_x86_64.whl)
Cleaning up...
Exception:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/pip/basecommand.py", line 122, in main
    status = self.run(options, args)
  File "/usr/lib/python2.7/dist-packages/pip/commands/install.py", line 304, in run
    requirement_set.prepare_files(finder, force_root_egg_info=self.bundle, bundle=self.bundle)
  File "/usr/lib/python2.7/dist-packages/pip/req.py", line 1198, in prepare_files
    do_download,
  File "/usr/lib/python2.7/dist-packages/pip/req.py", line 1376, in unpack_url
    self.session,
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 546, in unpack_http_url
    resp = session.get(target_url, stream=True)
  File "/usr/lib/python2.7/dist-packages/requests/sessions.py", line 477, in get
    return self.request('GET', url, **kwargs)
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 237, in request
    return super(PipSession, self).request(method, url, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/requests/sessions.py", line 465, in request
    resp = self.send(prep, **send_kwargs)
  File "/usr/lib/python2.7/dist-packages/requests/sessions.py", line 573, in send
    r = adapter.send(request, **kwargs)
  File "/usr/lib/python2.7/dist-packages/requests/adapters.py", line 419, in send
    raise ConnectTimeout(e, request=request)
ConnectTimeout: HTTPSConnectionPool(host='storage.googleapis.com', port=443): Max retries exceeded with url: /tensorflow/linux/cpu/tensorflow-0.5.0-cp27-none-linux_x86_64.whl (Caused by ConnectTimeoutError(<requests.packages.urllib3.connection.VerifiedHTTPSConnection object at 0x7f81d2b53e10>, 'Connection to storage.googleapis.com timed out. (connect timeout=15)'))

---

### Post by AkiraBergman on 2015-11-18
This seems to be a network problem. The link downloads on Chromium with Zenmate and not without.

---

