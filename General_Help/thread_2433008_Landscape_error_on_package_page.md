---
title: "Landscape error on package page"
date: 2019-12-12
forum: General Help
---

### Post by gregseth on 2019-12-12
I successfully set up one landscape server (called peanuts2) and added two computers.

When I try to access the "package" page ( [https://peanuts2/account/standalone/computers/packages](https://peanuts2/account/standalone/computers/packages) ) I get the system error message.

> 
System error
An unexpected error has occurred. This event has been logged.
We apologize for the inconvenience.
Please use Community Support for assistance or purchase an Ubuntu Advantage support contract for expedited technical help. 

The command [FONT=courier new]lsctl status[/FONT] shows the following python trace stating that some JSON object can't be decoded:


```
oct. 16 14:17:50 peanuts2 appserver-1[6330]: [https://peanuts2/account/standalone/computers/packages/index.html](https://peanuts2/account/standalone/computers/packages/index.html)
                                             Traceback (most recent call last):
                                               File "/usr/lib/python2.7/dist-packages/zope/publisher/publish.py", line 129, in publish
                                                 obj = request.traverse(obj)
                                               File "/usr/lib/python2.7/dist-packages/zope/publisher/browser.py", line 560, in traverse
                                                 ob = super(BrowserRequest, self).traverse(ob)
                                               File "/usr/lib/python2.7/dist-packages/zope/publisher/http.py", line 457, in traverse
                                                 ob = super(HTTPRequest, self).traverse(obj)
                                               File "/usr/lib/python2.7/dist-packages/zope/publisher/base.py", line 260, in traverse
                                                 obj = publication.traverseName(self, obj, entry_name)
                                               File "/usr/lib/python2.7/dist-packages/zope/app/publication/zopepublication.py", line 198, in traverseName
                                                 ob2 = adapter.publishTraverse(request, nm)
                                               File "/opt/canonical/landscape/canonical/routes/publisher.py", line 137, in publishTraverse
                                                 view = queryMultiAdapter((self.context, request), name=name)
                                               File "/usr/lib/python2.7/dist-packages/zope/component/_api.py", line 123, in queryMultiAdapter
                                                 return sitemanager.queryMultiAdapter(objects, interface, name, default)
                                               File "/usr/lib/python2.7/dist-packages/zope/interface/registry.py", line 359, in queryMultiAdapter
                                                 objects, interface, name, default)
                                               File "/usr/lib/python2.7/dist-packages/zope/interface/adapter.py", line 541, in queryMultiAdapter
                                                 result = factory(*objects)
                                               File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 70, in __init__
                                                 if self._has_no_packages:
                                               File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__
                                                 value = func(inst)
                                               File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 118, in _has_no_packages
                                                 no_packages_count = self._computer_counts["no-packages"]
                                               File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__
                                                 value = func(inst)
                                               File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 109, in _computer_counts
                                                 return self._counts[0]
                                               File "/usr/lib/python2.7/dist-packages/zope/cachedescriptors/property.py", line 71, in __get__
                                                 value = func(inst)
                                               File "/opt/canonical/landscape/canonical/landscape/ui/package/dashboard.py", line 105, in _counts
                                                 return self._search.get_computer_counts()
                                               File "/opt/canonical/landscape/canonical/landscape/model/package/search.py", line 221, in get_computer_counts
                                                 counts = self._get_computer_counts_external()
                                               File "/opt/canonical/landscape/canonical/landscape/model/package/search.py", line 301, in _get_computer_counts_external
                                                 account_id=account_id, computer_ids=computer_ids)
                                               File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 38, in query
                                                 return self._query(method, params)
                                               File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 60, in _query
                                                 raise PackageSearchRequestError(loads(error.body)["Error"])
                                               File "/usr/lib/python2.7/json/__init__.py", line 339, in loads
                                                 return _default_decoder.decode(s)
                                               File "/usr/lib/python2.7/json/decoder.py", line 364, in decode
                                                 obj, end = self.raw_decode(s, idx=_w(s, 0).end())
                                               File "/usr/lib/python2.7/json/decoder.py", line 382, in raw_decode
                                                 raise ValueError("No JSON object could be decoded")
                                             ValueError: No JSON object could be decoded
```
```

[...]

oct. 16 14:36:14 peanuts2 message-server-1[6522]: 21, 265822, 265824, 265826, 265829, 265830, (265832, 265837), (265839, 265844), 265846, (265848, 265851), 265853, 265856, (265858, 265865), (265867, 265869), 265871, (265874, 265878), (265880, 265883), 265885, 265886, 2658
                                                  (log message truncated, continued below)
                                                  Traceback (most recent call last):
                                                    File "/opt/canonical/landscape/canonical/landscape/message/apis.py", line 374, in _process_messages
                                                      self.handle(message["type"], message)
                                                    File "/opt/canonical/landscape/canonical/message/api.py", line 66, in handle
                                                      return handler(type, body)
                                                    File "/opt/canonical/landscape/canonical/message/handler.py", line 30, in __call__
                                                      return function(self.message_api, type, body)
                                                    File "/opt/canonical/landscape/canonical/lib/arguments.py", line 79, in replacement
                                                      return original(*new_args, **new_kwargs)
                                                    File "/opt/canonical/landscape/canonical/landscape/message/handlers/package.py", line 249, in handle_packages
                                                      not_held=sorted(buffer.not_held))
                                                    File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 38, in query
                                                      return self._query(method, params)
                                                    File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 60, in _query
                                                      raise PackageSearchRequestError(loads(error.body)["Error"])
                                                    File "/usr/lib/python2.7/json/__init__.py", line 339, in loads
                                                      return _default_decoder.decode(s)
                                                    File "/usr/lib/python2.7/json/decoder.py", line 364, in decode
                                                      obj, end = self.raw_decode(s, idx=_w(s, 0).end())
                                                    File "/usr/lib/python2.7/json/decoder.py", line 382, in raw_decode
                                                      raise ValueError("No JSON object could be decoded")
                                                  ValueError: No JSON object could be decoded
```


Any idea about how to get things working?

---

