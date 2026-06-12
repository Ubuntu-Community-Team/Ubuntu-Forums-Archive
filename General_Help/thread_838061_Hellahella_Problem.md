---
title: "Hellahella Problem"
date: 2008-06-23
forum: General Help
---

### Post by ttsk8r on 2008-06-23
When I type  "paster serve hella.ini" The following is outputted

```

/usr/lib/python2.5/site-packages/hellahella-0.1dev_r1088-py2.5.egg/hellahella/config/environment.py:32: DeprecationWarning: The pylons.config.Config object is deprecated. Please load the environment configuration via the pylons.config object in config/environment.py instead, .e.g:

    from pylons import config

And in in the load_environment function:

    config['routes.map'] = map

    # The template options
    tmpl_options = config['buffet.template_options']

    # CONFIGURATION OPTIONS HERE (note: all config options will override any
    # Pylons config options)

See the default config/environment.py created via the "paster create -t pylons"
command for a full example.

  return pylons.config.Config(tmpl_options, map, paths)
/usr/lib/python2.5/site-packages/hellahella-0.1dev_r1088-py2.5.egg/hellahella/config/middleware.py:37: DeprecationWarning: Pylons 0.9.6 and above projects must explicitly initialize the helpers and g objects in their config/environment.py. Please no longer specify the helpers and g keyword arguments to PylonsApp in your config/middleware.py: instead, update your config/environment.py with:

    from pylons import config

    import hellahella.lib.app_globals as app_globals
    import hellahella.lib.helpers

And add the following lines to the load_environment function:

    # Initialize config with the basic options
    config.init_app(global_conf, app_conf, package='hellahella',
                    template_engine='pylonsmyghty', paths=paths)

    config['pylons.g'] = app_globals.Globals()
    config['pylons.h'] = hellahella.lib.helpers
    config['routes.map'] = make_map()

See the default config/environment.py created via the "paster create -t pylons"
command for a full example.

  g=app_globals.Globals)
/usr/lib/python2.5/site-packages/hellahella-0.1dev_r1088-py2.5.egg/hellahella/config/middleware.py:37: DeprecationWarning: Handling conf arguments in your app_globals __init__ function is no longer required. Please update your config/app_globals.py with:
    from pylons import config

    class Globals(object):
        def __init__(self):
            pass

And use the config object in your Globals instance.

  g=app_globals.Globals)
Traceback (most recent call last):
  File "/usr/bin/paster", line 8, in <module>
    load_entry_point('PasteScript==1.6.3', 'console_scripts', 'paster')()
  File "/usr/lib/python2.5/site-packages/PasteScript-1.6.3-py2.5.egg/paste/script/command.py", line 79, in run
    invoke(command, command_name, options, args[1:])
  File "/usr/lib/python2.5/site-packages/PasteScript-1.6.3-py2.5.egg/paste/script/command.py", line 118, in invoke
    exit_code = runner.run(args)
  File "/usr/lib/python2.5/site-packages/PasteScript-1.6.3-py2.5.egg/paste/script/command.py", line 213, in run
    result = self.command()
  File "/usr/lib/python2.5/site-packages/PasteScript-1.6.3-py2.5.egg/paste/script/serve.py", line 251, in command
    relative_to=base, global_conf=vars)
  File "/usr/lib/python2.5/site-packages/PasteScript-1.6.3-py2.5.egg/paste/script/serve.py", line 278, in loadapp
    **kw)
  File "/usr/lib/python2.5/site-packages/PasteDeploy-1.3.2-py2.5.egg/paste/deploy/loadwsgi.py", line 204, in loadapp
    return loadobj(APP, uri, name=name, **kw)
  File "/usr/lib/python2.5/site-packages/PasteDeploy-1.3.2-py2.5.egg/paste/deploy/loadwsgi.py", line 225, in loadobj
    return context.create()
  File "/usr/lib/python2.5/site-packages/PasteDeploy-1.3.2-py2.5.egg/paste/deploy/loadwsgi.py", line 625, in create
    return self.object_type.invoke(self)
  File "/usr/lib/python2.5/site-packages/PasteDeploy-1.3.2-py2.5.egg/paste/deploy/loadwsgi.py", line 110, in invoke
    return fix_call(context.object, context.global_conf, **context.local_conf)
  File "/usr/lib/python2.5/site-packages/PasteDeploy-1.3.2-py2.5.egg/paste/deploy/util/fixtypeerror.py", line 57, in fix_call
    val = callable(*args, **kw)
  File "/usr/lib/python2.5/site-packages/hellahella-0.1dev_r1088-py2.5.egg/hellahella/config/middleware.py", line 37, in make_app
    g=app_globals.Globals)
  File "/usr/lib/python2.5/site-packages/Pylons-0.9.6.2-py2.5.egg/pylons/wsgiapp.py", line 299, in __init__
    from beaker.middleware import SessionMiddleware
  File "/usr/lib/python2.5/site-packages/Myghty-1.1-py2.5.egg/myghty/importer.py", line 54, in import_module
    return builtin_importer(name, globals, locals, fromlist)
  File "/usr/lib/python2.5/site-packages/Beaker-0.9.5-py2.5.egg/beaker/middleware.py", line 12, in <module>
    from beaker.cache import CacheManager
  File "/usr/lib/python2.5/site-packages/Myghty-1.1-py2.5.egg/myghty/importer.py", line 54, in import_module
    return builtin_importer(name, globals, locals, fromlist)
  File "/usr/lib/python2.5/site-packages/Beaker-0.9.5-py2.5.egg/beaker/cache.py", line 32, in <module>
    import beaker.ext.google as google
  File "/usr/lib/python2.5/site-packages/Myghty-1.1-py2.5.egg/myghty/importer.py", line 54, in import_module
    return builtin_importer(name, globals, locals, fromlist)
  File "/usr/lib/python2.5/site-packages/Beaker-0.9.5-py2.5.egg/beaker/ext/google.py", line 1, in <module>
    from __future__ import absolute_import
TypeError: import_module() takes at most 4 arguments (5 given); got ({'userna...er'}, app_instance_uuid=..., cache_dir=..., session_key=..., session_secret=...), wanted (global_conf, full_stack=True, **app_conf)
```

---

### Post by ttsk8r on 2008-06-24
Anyone?

---

