---
title: "Ubuntu 14.04 Software Updater killed awscli"
date: 2015-09-26
forum: General Help
---

### Post by jpapa on 2015-09-26
This morning I took an update form Software Updater and my aws cli install promptly broke and I can't get it working again. 

I tried purging, autoremoving and reinstalling but the same thing happens.

~$ aws
Traceback (most recent call last):
  File "/usr/bin/aws", line 23, in <module>
    sys.exit(main())
  File "/usr/bin/aws", line 19, in main
    return awscli.clidriver.main()
  File "/usr/share/awscli/awscli/clidriver.py", line 44, in main
    driver = create_clidriver()
  File "/usr/share/awscli/awscli/clidriver.py", line 53, in create_clidriver
    event_hooks=emitter)
  File "/usr/share/awscli/awscli/plugin.py", line 49, in load_plugins
    plugin.awscli_initialize(event_hooks)
  File "/usr/share/awscli/awscli/handlers.py", line 73, in awscli_initialize
    register_removals(event_handlers)
  File "/usr/share/awscli/awscli/customizations/removals.py", line 32, in register_removals
    'verify-email-address'])
  File "/usr/share/awscli/awscli/customizations/removals.py", line 45, in remove
    self._create_remover(remove_commands))
  File "/usr/lib/python3/dist-packages/botocore/hooks.py", line 64, in register
    self._verify_accept_kwargs(handler)
  File "/usr/lib/python3/dist-packages/botocore/hooks.py", line 84, in _verify_accept_kwargs
    argspec = inspect.getargspec(func)
  File "/usr/lib/python3.4/inspect.py", line 936, in getargspec
    raise ValueError("Function has keyword-only arguments or annotations"
ValueError: Function has keyword-only arguments or annotations, use getfullargspec() API which can support them

---

### Post by jpapa on 2015-09-26
I was able to get it back by doing apt-get purge, then apt-get autoremove and then installing via pip instead of apt-get.

Still would be curious to know why reinstalling via apt-get didn't fix it.

---

### Post by ayqazi on 2015-09-30
It seems Python upgrades have a habit of breaking backwards compatibility with older versions.... it's happened before: [https://github.com/aws/aws-cli/issues/800](https://github.com/aws/aws-cli/issues/800)

They probably fixed it in the latest version which you installed via pip, but that new version has not trickled into the apt repository yet.

---

