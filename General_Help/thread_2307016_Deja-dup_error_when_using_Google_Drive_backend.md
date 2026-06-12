---
title: "Deja-dup error when using Google Drive backend"
date: 2015-12-21
forum: General Help
---

### Post by TriforceOfKirby on 2015-12-21
I was using dconf-editor and noticed org.gnome.deja-dup Backend had 'gdrive' as an option. After opening deja-dup it asked me to login to Google Drive. After logging in and it tries to backup I get an error:
```
Traceback (most recent call last):  File "/usr/bin/duplicity", line 1519, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1513, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1354, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 1062, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 223, in get_backend
    obj = get_backend_object(url_string)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 209, in get_backend_object
    return factory(pu)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/gdocsbackend.py", line 54, in __init__
    self._authorize(parsed_url.username + '@' + parsed_url.hostname, self.get_password())
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/gdocsbackend.py", line 134, in _authorize
    captcha_response=captcha_response)
  File "/usr/lib/python2.7/dist-packages/gdata/client.py", line 441, in client_login
    captcha_token=captcha_token, captcha_response=captcha_response)
  File "/usr/lib/python2.7/dist-packages/gdata/client.py", line 373, in request_client_login_token
    response, ClientLoginFailed, response_body)
ClientLoginFailed: Server responded to ClientLogin request: 404, https://developers.google.com/accounts/docs/AuthForInstalledApps
```

---

### Post by TriforceOfKirby on 2015-12-31
bump

---

### Post by TriforceOfKirby on 2016-01-11
bump; any fixes?

---

