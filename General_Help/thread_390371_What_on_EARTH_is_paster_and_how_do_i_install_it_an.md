---
title: "What on EARTH is paster? and how do i install it and fix my error"
date: 2007-03-21
forum: General Help
---

### Post by mesach on 2007-03-21
I'm trying to install hellahella on my computer and i'm getting this error when i run the command  paster setup-app hella.ini

```
~$ paster setup-app hella.ini
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
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 441, in command
    conf = appconfig(config_spec, relative_to=os.getcwd())
  File "/usr/lib/python2.4/site-packages/PasteDeploy-1.1-py2.4.egg/paste/deploy/loadwsgi.py", line 204, in appconfig
    global_conf=global_conf)
  File "/usr/lib/python2.4/site-packages/PasteDeploy-1.1-py2.4.egg/paste/deploy/loadwsgi.py", line 237, in loadcontext
    global_conf=global_conf)
  File "/usr/lib/python2.4/site-packages/PasteDeploy-1.1-py2.4.egg/paste/deploy/loadwsgi.py", line 264, in _loadconfig
    loader = ConfigLoader(path)
  File "/usr/lib/python2.4/site-packages/PasteDeploy-1.1-py2.4.egg/paste/deploy/loadwsgi.py", line 327, in __init__
    raise OSError(

```

I have looked up "paster ubuntu" and "apt-get paster" both here and in google and the best i can get is a tutorial on installing hellahella that i'm using which goes like this

*********************
sudo python ez_setup.py -U hellahella==dev

hellahella and it's dependancies are installed.

paster make-config hellahella hella.ini

Then edit hella.ini to setup your hellanzb connection info and login information. The defaults correspond to hellanzb.py 's defaults.

Once you've setup hella.ini you are near to the completion of installation

paster setup-app hella.ini

paster serve hella.ini

You now should be able to login to hellahella by opening [http://localhost:5000/](http://localhost:5000/) in your browser.
*********************

NO ONE mentions anything about getting an error when running the paster make-config hellahella hella.ini command.

Can anyone help me get this installed?

---

### Post by KrakensDen on 2007-03-22
Have you installed Pylons (The framework that hellahella runs on top of)?

---

### Post by mesach on 2007-03-22
I dont remember ever installing it(and that means I did not do it) but here is what i got when i tried easy_install Pylons

Searching for Pylons
Best match: Pylons 0.9.4.1
Processing Pylons-0.9.4.1-py2.4.egg
Pylons 0.9.4.1 is already the active version in easy-install.pth

Using /usr/lib/python2.4/site-packages/Pylons-0.9.4.1-py2.4.egg
Processing dependencies for Pylons

so then i re run the paster setup-app hella.ini

and still get the same problem.

---

### Post by toliman on 2007-05-09
> **mesach said:**
> I dont remember ever installing it(and that means I did not do it) but here is what i got when i tried easy_install Pylons

Searching for Pylons
Best match: Pylons 0.9.4.1
Processing Pylons-0.9.4.1-py2.4.egg
Pylons 0.9.4.1 is already the active version in easy-install.pth

Using /usr/lib/python2.4/site-packages/Pylons-0.9.4.1-py2.4.egg
Processing dependencies for Pylons

so then i re-run the paster setup-app hella.ini

and still get the same problem.

i just ran into this app  from a fresh install of feisty. 

hellanzb works ok from the svn downloaded version 0.13, and i know that downloads OK, (badly made par2/nzb files cause it to crashes occasionally), but downloads ok. 

he init.d script from the HOWTO also works, and i&#314;l add the paster serve hella.ini line to the script so i can start it as a daemon.

as a backup, zussaweb also works when i unpacked it to /var/www/, so i know it&#347; working well, just in case python dies or something happens.

now, having not really got into python, i installed python-pastescript setuptools and python-dev as recommended, and ran those install commands, but things stopped working. 

after a while i tried sudo easy_install hellahella==dev which is really calling the ez_setup.py script using one of the updated python modules. after a break, i came back and ran sudo easy_install <module>  e.g. decorator, and 5 mins + easy_install <whatever> the other objectionable python bits, it worked.

probably not the most elegant way to get things installed, but it works. :)

---

