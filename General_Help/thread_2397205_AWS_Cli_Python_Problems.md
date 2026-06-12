---
title: "AWS Cli Python Problems"
date: 2018-07-26
forum: General Help
---

### Post by emackey3k on 2018-07-26
I installed aws-cli via apt.  When I try to run the configure or just show the version I get the below error.  

Traceback (most recent call last):
  File "/usr/local/bin/aws", line 19, in <module>
    import awscli.clidriver
  File "/usr/local/aws/local/lib/python2.7/site-packages/awscli/clidriver.py", line 15, in <module>
    import logging
  File "/usr/lib/python2.7/logging/__init__.py", line 26, in <module>
    import sys, os, time, cStringIO, traceback, warnings, weakref, collections
  File "/usr/lib/python2.7/weakref.py", line 14, in <module>
    from _weakref import (
ImportError: cannot import name _remove_dead_weakref

The issue might be that it is using python 2.7 instead of python 3?

Here are the versions:
Ubuntu 18.04.1 LTS
awscli 1.14.44-1ubuntu1
Python 3.6.5
Python 2.7.15rc1

Any help would be appreciated.

---

