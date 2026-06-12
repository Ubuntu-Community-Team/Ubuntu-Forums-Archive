---
title: "hellahella errors?"
date: 2007-03-12
forum: General Help
---

### Post by trmentry on 2007-03-12
I got hellahella installed for hellanzb but when I go to try and make the hella.ini file I get the following.

```

sudo paster make-config hellahella hella.ini
Distribution already installed:
  hellahella 0.1dev-r1002 from /usr/lib/python2.4/site-packages/hellahella-0.1dev_r1002-py2.4.egg
Traceback (most recent call last):
  File "/usr/bin/paster", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/command.py", line 76, in run
    invoke(command, command_name, options, args[1:])
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/command.py", line 115, in invoke
    exit_code = runner.run(args)
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/appinstall.py", line 65, in run
    return super(AbstractInstallCommand, self).run(new_args)
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/command.py", line 210, in run
    result = self.command()
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/appinstall.py", line 325, in command
    self.installer.write_config(self, self.config_file, self.vars)
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/appinstall.py", line 501, in write_config
    command.ensure_file(filename, self.config_content(command, vars))
  File "/usr/lib/python2.4/site-packages/PasteScript-1.3-py2.4.egg/paste/script/appinstall.py", line 534, in config_content
    tmpl = Cheetah.Template(self.dist.get_metadata(meta_name),
AttributeError: 'module' object has no attribute 'Template'
```

Anyone have some suggestions?

Thanks

---

### Post by mesach on 2007-03-20
I have this exact same problem... 

Anyone have any solution on what causes it?

---

### Post by mesach on 2007-03-20
Here is the error I am getting... I have cheetah installed the OP apparently does not

```
Distribution already installed:
  hellahella 0.1dev-r1002 from /usr/lib/python2.4/site-packages/hellahella-0.1dev_r1002-py2.4.egg
Traceback (most recent call last):
  File "/usr/bin/paster", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 76, in run
    invoke(command, command_name, options, args[1:])
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 115, in invoke
    exit_code = runner.run(args)
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 63, in run
    return super(AbstractInstallCommand, self).run(new_args)
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 210, in run
    result = self.command()
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 289, in command
    self.installer = self.get_installer(
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 228, in get_installer
    installer_class = distro.load_entry_point(
  File "/usr/lib/python2.4/site-packages/setuptools-0.6c5-py2.4.egg/pkg_resources.py", line 2097, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.4/site-packages/setuptools-0.6c5-py2.4.egg/pkg_resources.py", line 1829, in load
    if require: self.require(env, installer)
  File "/usr/lib/python2.4/site-packages/setuptools-0.6c5-py2.4.egg/pkg_resources.py", line 1842, in require
    working_set.resolve(self.dist.requires(self.extras),env,installer))
  File "/usr/lib/python2.4/site-packages/setuptools-0.6c5-py2.4.egg/pkg_resources.py", line 487, in resolve
    raise VersionConflict(dist,req) # XXX put more info here
pkg_resources.VersionConflict: (PasteScript 0.9.8 (/usr/lib/python2.4/site-packages), Requirement.parse('PasteScript>=1.0'))

```

---

### Post by dmce on 2007-03-24
Poster 1 and 2

I had this problem. Upgrading Paste and PasteScript to trunk release seemed to resolve.

Have a look here on how to do that:

[http://pythonpaste.org/download/](http://pythonpaste.org/download/)

I done

svn co [http://svn.pythonpaste.org/Paste/trunk](http://svn.pythonpaste.org/Paste/trunk) Paste
easy_install Paste==dev
svn co [http://svn.pythonpaste.org/Paste/Script/trunk](http://svn.pythonpaste.org/Paste/Script/trunk) PasteScript
easy_install PasteScript==dev

---

