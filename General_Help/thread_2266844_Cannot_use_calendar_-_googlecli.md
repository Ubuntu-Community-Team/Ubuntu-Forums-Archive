---
title: "Cannot use calendar - googlecli"
date: 2015-02-25
forum: General Help
---

### Post by CkDGTAT on 2015-02-25
Hi,

```
google calendar add event
```

```
    File /usr/bin/google, line 991, in <module>    main()
  File /usr/bin/google, line 977, in main
    run_once(options, args)
  File /usr/bin/google, line 763, in run_once
    task.run(client, options, args)
  File /usr/lib/pymodules/python2.7/googlecl/calendar/__init__.py, line 330, in _run_add
    results = client.quick_add_event(events_list, cal.user)
  File /usr/lib/pymodules/python2.7/googlecl/calendar/service.py, line 277, in quick_add_event
    USER_BATCH_URL_FORMAT % calendar_user)
  File /usr/lib/python2.7/dist-packages/gdata/calendar/service.py, line 445, in ExecuteBatch
    return self.Post(batch_feed, url, converter=converter)
  File /usr/lib/pymodules/python2.7/googlecl/service.py, line 69, in retry_post
    return self.retry_operation(*args, **kwargs)
  File /usr/lib/pymodules/python2.7/googlecl/base.py, line 394, in retry_operation
    raise err
gdata.service.RequestError: {'status': 403, 'body': '<HTML>
<HEAD>
<TITLE>Forbidden</TITLE>
</HEAD>
<BODY BGCOLOR=#FFFFFF TEXT=#000000>
<H1>Forbidden</H1>
<H2>Error 403</H2>
</BODY>
</HTML>
', 'reason': 'Forbidden'}



```

---

