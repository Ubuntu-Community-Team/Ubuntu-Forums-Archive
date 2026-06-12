---
title: "Python cannot find installed package"
date: 2018-02-18
forum: General Help
---

### Post by John_Rose on 2018-02-18
Hello, I am using Ubuntu 14.04 LTS and am trying to get yowsup (Whatsapp client simulator which runs under python) working. I followed the instructions at [https://iamjagjeetubhi.wordpress.com/2017/09/21/how-to-use-yowsup-the-python-whatsapp-library-in-ubuntu/](https://iamjagjeetubhi.wordpress.com/2017/09/21/how-to-use-yowsup-the-python-whatsapp-library-in-ubuntu/) and successfully did the installation and registration, but when I try to do the tests with the command:

 ```
 **whatsapp$ yowsup-cli demos --yowsup --config config**
```  
 
  I get the following output with error message:
 
 ```
Traceback (most recent call last):

   File "/usr/local/bin/yowsup-cli", line 4, in <module>
     import pkg_resources
   File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2749, in <module>
     working_set = WorkingSet._build_master()
   File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 446, in _build_master
     return cls._build_from_requirements(__requires__)
   File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 459, in _build_from_requirements
     dists = ws.resolve(reqs, Environment())
   File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 628, in resolve
     raise DistributionNotFound(req)
  pkg_resources.DistributionNotFound: six==1.10

```  
 
      I'm using python 2.7.6 (most recent for the distribution) and had the latest Ubuntu python-six package installed (1.5.2-1ubuntu1). I installed pip and virtualenv and installed version 1.10.0 of six (python-six package) in the virtual enviroment, but I still get the same message. I have tried resetting the paths through appending to $PYTHONPATH and by installing a .pth file but same result.

Unless I have made a mistake (or not done enough) in resetting the paths to find the added python module, I have wondered whether there may be one of the following issues:
i) maybe I should have done the entire yowsup set-up process in the Virtual Environment instead of creating it after I had the problem?
ii) maybe I should have uninstalled the old six package in the Virtual Environment before installing the upgrade (but not clear that pip can uninstall it)?
iii) maybe > raise DistributionNotFound(req) pkg_resources.DistributionNotFound means more than simply a missing package?
Could you please advise?

---

### Post by John_Rose on 2018-02-18
Sorry to bother, I have solved the problem. The python application created in the normal Ubuntu environment expected the needed resources to be in "/usr/lib/python2.7/dist-packages/pkg_resources.py" instead of in the Virtual Environment into which the upgraded "six" package had been installed. I created an new Virtual Environment and in that environment installed the missing resource with pip before building and installing the application. The application now seems to be working normally when called from the Virtual Environment. So if you are using a Virtual Enviroment (virtualenv) you should install your python modules exclusively with pip (with the Environment activated) and not mix with apt-get calls for modules available through pip.

---

