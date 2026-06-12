---
title: "Ubuntu 13.04 software center not working"
date: 2013-06-04
forum: General Help
---

### Post by Derelinquat fenestras on 2013-06-04
Hello all,

I ran 

sudo apt-get upgrade 

yesterday, and scanning the output, I noticed that both ubuntu-desktop and software-center packages were removed.

I attempted to reinstall them, but could not due to errors.  Today I was able to reinstall them but during the install there were numerous packages not found in the output for software-center install.

It said it installed successfully, but when I try to initialize the software center, it opens briefly then closes, then give an apport crash report...

I have attempted:

1) sudo apt-get install -f software-center
    which outputs:  software-center is already the newest version.2) fix broken packages via synaptic --> said it was successful
3) sudo dpkg-reconfigure software-center --force and got this output:
```

Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.

```


When I try to open software-center via terminal, I get this output:
```

2013-06-04 10:35:42,660 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://127.0.0.1:9666/'
2013-06-04 10:35:44,701 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-06-04 10:35:44,761 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-06-04 10:35:44,761 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-06-04 10:35:45,323 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-06-04 10:35:45,820 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 14}']'
2013-06-04 10:35:45,822 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://reviews.ubuntu.com/reviews/api/1.0/review-stats/any/any/:](http://reviews.ubuntu.com/reviews/api/1.0/review-stats/any/any/:) Connection refused
'
2013-06-04 10:35:45,938 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'get_usefulness', '{"username": "JsLAbf4"}']'
2013-06-04 10:35:45,939 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://reviews.ubuntu.com/reviews/api/1.0/usefulness/?username=JsLAbf4:](http://reviews.ubuntu.com/reviews/api/1.0/usefulness/?username=JsLAbf4:) Connection refused
'


(software-center:3152): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1683 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
jacob@jacob-laptop:~$ 2013-06-04 10:36:01,232 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterAgentAPI', 'available_apps', '{"lang": "en", "series": "raring", "arch": "i386"}']'
2013-06-04 10:36:01,233 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:](http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:) Connection refused
'
2013-06-04 10:36:01,234 - softwarecenter.db.update - WARNING - update_from_software_center_agent: error: 'WARNING:__main__:connecting to [http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:](http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:) Connection refused\n'

```
Running a little bit low on Ideas and would greatly appreciate any help from the community!

Thanks

---

### Post by sanderj on 2013-06-04
I would first do a update & upgrade from the command line:

```
sudo apt-get update && sudo apt-get upgrade
```

And then again.

Does that run without errors?

---

### Post by Derelinquat fenestras on 2013-06-05
Thanks for the reply!

I have done that and there appear to be no errors, however, none of the updates seemed relevant to the software center.
And when it seems like the upgrade is almost done, the last 2 lines of the output read:

ldconfig deferred processing now taking place
Error: Timeout was reached

that actually has been occurring intermittently for a little while.  I don't know exactly what that means, but it never seems to affect anything, because I was usually re-running the update/upgrade afterward to see if anything went wrong, and it always says 0 upgrades...

And after the upgrade, when I attempt to initialize the software center via the terminal, I continue to get error messages:

2013-06-05 22:07:45,221 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://127.0.0.1:9666/'
2013-06-05 22:07:49,837 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-06-05 22:07:49,954 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-06-05 22:07:49,953 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-06-05 22:07:50,892 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-06-05 22:07:51,945 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 16}']'
2013-06-05 22:07:51,946 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://reviews.ubuntu.com/reviews/api/1.0/review-stats/any/any/:](http://reviews.ubuntu.com/reviews/api/1.0/review-stats/any/any/:) Connection refused
'
2013-06-05 22:07:51,947 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'get_usefulness', '{"username": "JsLAbf4"}']'
2013-06-05 22:07:51,948 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://reviews.ubuntu.com/reviews/api/1.0/usefulness/?username=JsLAbf4:](http://reviews.ubuntu.com/reviews/api/1.0/usefulness/?username=JsLAbf4:) Connection refused
'
2013-06-05 22:08:11,911 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterAgentAPI', 'available_apps', '{"lang": "en", "series": "raring", "arch": "i386"}']'
2013-06-05 22:08:11,912 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:](http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:) Connection refused
'
2013-06-05 22:08:11,913 - softwarecenter.db.update - WARNING - update_from_software_center_agent: error: 'WARNING:__main__:connecting to [http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:](http://software-center.ubuntu.com/api/2.0/applications/en/ubuntu/raring/i386/:) Connection refused\n'
2013-06-05 22:08:12,013 - softwarecenter.db.utils - INFO - software-center-agent finished with status 1
2013-06-05 22:08:40,436 - softwarecenter.backend.recagent - INFO - Submitting recommendations profile to the server
2013-06-05 22:09:05,877 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:05,876 - debtagshw.opengl - INFO - gl vendor: Intel Open Source Technology Center
2013-06-05 22:09:05,881 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:05,880 - debtagshw.opengl - INFO - gl renderer: Mesa DRI Intel(R) IGD x86/MMX/SSE2
2013-06-05 22:09:05,883 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:05,883 - debtagshw.opengl - INFO - gl version: 1.4 Mesa 9.1.1
2013-06-05 22:09:06,169 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,167 - debtagshw.opengl - INFO - gl vendor: Intel Open Source Technology Center
2013-06-05 22:09:06,172 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,171 - debtagshw.opengl - INFO - gl renderer: Mesa DRI Intel(R) IGD x86/MMX/SSE2
2013-06-05 22:09:06,174 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,174 - debtagshw.opengl - INFO - gl version: 1.4 Mesa 9.1.1
2013-06-05 22:09:06,374 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,373 - debtagshw.opengl - INFO - gl vendor: Intel Open Source Technology Center
2013-06-05 22:09:06,378 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,377 - debtagshw.opengl - INFO - gl renderer: Mesa DRI Intel(R) IGD x86/MMX/SSE2
2013-06-05 22:09:06,381 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,380 - debtagshw.opengl - INFO - gl version: 1.4 Mesa 9.1.1
2013-06-05 22:09:06,570 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,569 - debtagshw.opengl - INFO - gl vendor: Intel Open Source Technology Center
2013-06-05 22:09:06,574 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,573 - debtagshw.opengl - INFO - gl renderer: Mesa DRI Intel(R) IGD x86/MMX/SSE2
2013-06-05 22:09:06,576 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/debtagshw/opengl.py', 146, '_get_opengl_vendor_renderer_version_tuple')'
2013-06-05 22:09:06,576 - debtagshw.opengl - INFO - gl version: 1.4 Mesa 9.1.1
2013-06-05 22:09:08,283 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterRecommenderAPI', 'recommend_app', '{"pkgname": "mafagafo-killing-center"}']'
2013-06-05 22:09:08,285 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to [http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:](http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:) Connection refused
'
2013-06-05 22:09:08,288 - softwarecenter.db.categories - WARNING - Error while accessing the recommender service: WARNING:__main__:connecting to [http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:](http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:) Connection refused


2013-06-05 22:09:08,289 - softwarecenter.ui.gtk3.widgets.recommendations - WARNING - Error while accessing the recommender agent: WARNING:__main__:connecting to [http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:](http://rec.ubuntu.com/api/1.0/recommend_app/mafagafo-killing-center/:) Connection refused

... But, the software center does open, but the graphics/fonts appear a little scrambled...

---

### Post by MARP1961 on 2013-06-06
Me too. No Software Centre. I have removed and reinstalled it via Synaptic and it still won't work. I'm running Ubuntu Gnome 13.04 with Nautilus 3.8

---

### Post by Derelinquat fenestras on 2013-06-06
Hello!
I did get mine working again without much work... 

I just ran:

sudo apt-get update
sudo apt-get upgrade

several days in a row and eventually it started up again.  Might be just an issue where the new libraries are not out yet.

Good luck...

---

### Post by MARP1961 on 2013-06-06
Many thanks for that. Until then we can always use Synaptic Package Manager or the 'sudo apt-get install .....' command in Terminal.

---

### Post by matt_symes on 2013-06-06
Hi

Try deleting or renaming (renaming may be the safer option as you can always rename it back) the software-center cache in your home directory.

It will be in one of the hidden directories: maybe ~/.cache or some such.

I think maybe 

```
mv ~/.cache/software-center{,.bak}
```

Then try software center again.

Incedently, create a new user and log into that user. Can you use the software center then ?

Kind regards

---

### Post by Derelinquat fenestras on 2013-06-07
Bumping Thread

---

### Post by matt_symes on 2013-06-07
Hi

> for matt_symes:  just read your reply on my forum thread... did you mean to rename the cashe folder for software-center?

Yep. Please rename the cache folder for the software center. Let's see what affect that has.

```
mv ~/.cache/software-center{,.bak}
```

Kind regards

---

### Post by MARP1961 on 2013-06-10
> **matt_symes said:**
> Hi

Try deleting or renaming (renaming may be the safer option as you can always rename it back) the software-center cache in your home directory.

It will be in one of the hidden directories: maybe ~/.cache or some such.

I think maybe 

```
mv ~/.cache/software-center{,.bak}
```

Then try software center again.

Incedently, create a new user and log into that user. Can you use the software center then ?

Kind regards I tried renaming the  software-center folder inside the .cache folder but with no success. Software Center seems to start then closes.

---

### Post by MARP1961 on 2013-06-10
I'll now create a new user and try again. Will report back.

---

### Post by MARP1961 on 2013-06-10
No luck with a New User. I've tried removing and reinstalling Software Center. Still no luck.

---

### Post by matt_symes on 2013-06-10
Hi

Try running software center from the terminal. 

Do you get any kind of backtrace ?

If so then post it back here.

Kind regards

---

### Post by yotamtly on 2013-09-24
hi, thanks, tried it, seems to worked well, but got this warning (repeated 3 times one after ther other):

WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application

---

### Post by yotamtly on 2013-09-24
hi, thanks, tried it, seems to worked well, but got this warning (repeated 3 times one after ther other):

WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:mad:-sonicvisualiser-layer.desktop'  could not be read correctly. The application associated with this file  will not be included in the software catalog. Please consider raising a  bug report for this issue with the maintainer of that application

---

