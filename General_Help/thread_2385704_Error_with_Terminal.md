---
title: "Error with Terminal"
date: 2018-02-23
forum: General Help
---

### Post by delsystem32 on 2018-02-23
I am trying to install cuckoo sandbox. I typed:

sudo pip install -U cuckoo

and terminal says "The directory /home/delsstem32/.cache/pip/http" or its parent directory is not owned by the curent user pr the cache has been disabled. Please check permissions and owner of that directory. 
If executing pip with sudo, you may want to use sudo's -H flag."

What do I do ? I am the only user and have no clue how to use -H flag or how I don't own the directory. Plz help thank.

---

### Post by delsystem32 on 2018-02-23
When I ignore the directory issue and continue installing I get this
```
      File "/usr/lib/python2.7/distutils/command/build_ext.py", line 340, in run
        self.build_extensions()
      File "/tmp/pip-build-XhWczw/pillow/setup.py", line 512, in build_extensions
        ' using --disable-%s, aborting' % (f, f))
    ValueError: jpeg is required unless explicitly disabled using --disable-jpeg, aborting
    
    ----------------------------------------
Command "/usr/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-XhWczw/pillow/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record /tmp/pip-4uBfkG-record/install-record.txt --single-version-externally-managed --compile" failed with error code 1 in /tmp/pip-build-XhWczw/pillow/

```

---

### Post by #&amp;thj^% on 2018-02-23
Did you ever Create a user for Cuckoo.

```
useradd cuckoo
```
And Create a folder?

and make sure that the user who is going to run cuckoo is the owner of the files.

```
chown -R cuckoo:cuckoo <path/to/cuckoo/folder>
```

Might be better to start again with this how to Read Thoroughly: [https://medium.com/@warunikaamali/cuckoo-sandbox-installation-guide-d7a09bd4ee1f](https://medium.com/@warunikaamali/cuckoo-sandbox-installation-guide-d7a09bd4ee1f)
And the -H Flag
```
-H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.

```

---

### Post by steeldriver on 2018-02-23
I'm not a pip expert, but shouldn't you **either **use

```

pip install -U cuckoo

```

(to install locally) **or**

```

sudo pip install cuckoo

```

(to install site-wide) - using sudo together with -U seems like a bad idea (which is  essentially what the error message is telling you)

---

### Post by delsystem32 on 2018-02-23
Thanks a lot guys.

---

