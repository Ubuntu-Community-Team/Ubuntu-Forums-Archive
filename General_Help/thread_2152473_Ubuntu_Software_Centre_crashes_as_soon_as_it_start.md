---
title: "Ubuntu Software Centre crashes as soon as it starts?"
date: 2013-06-07
forum: General Help
---

### Post by Moose on 2013-06-07
Hey, basically, this is what happens:

[LIST]
[*]Opens Software Centre
[*]It opens normally
[*]It closes after about 2-3 seconds
[*]Doesn't say anything about a crash report or anything like that.
[/LIST]
I have tried re-installing USC and it still does it. Any help?

---

### Post by 2F4U on 2013-06-08
Have you tried starting Software Center out of a terminal? It may display error messages when started from terminal. Is apt-get through terminal working?

---

### Post by Moose on 2013-06-08
No. I installed Ubuntu Software Centre using Ubuntu Software Centre.. -.-

***Of course*** I used the Terminal. And no, it doesn't make a difference.

---

### Post by plucky on 2013-06-08
> Of course I used the Terminal. And no, it doesn't make a difference. 

Were there any error messages?

What happens if you run ```
sudo apt-get update
``` in a terminal window?

---

### Post by Moose on 2013-06-08
1. There were no errors.
2. It updated..? And it fixed nothing.

---

### Post by deadflowr on 2013-06-08
I think 2F4U meant try launching it with the command
software-center, or software-centre.
And see what the output is.
You should be getting some sort of output.

---

### Post by Moose on 2013-06-09
Here's the output:

```
anthony@Allwissend:~$ software-centreNo command 'software-centre' found, did you mean:
 Command 'software-center' from package 'software-center' (main)
software-centre: command not found
anthony@Allwissend:~$ software-center
2013-06-09 13:58:38,141 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-06-09 13:58:45,114 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-06-09 13:58:46,239 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-06-09 13:58:46,256 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-06-09 13:58:46,340 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-06-09 13:58:46,340 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-06-09 13:58:46,529 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()


(software-center:7444): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 2463 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap
anthony@Allwissend:~$ 



```

---

### Post by deadflowr on 2013-06-10
Info bump for you.

I found two bugs on the issue

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1165939](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1165939)

And this one, which contains more commenting, which might help

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1163886](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1163886)

Don't know how helpful it will be, but it's something.

---

### Post by Moose on 2013-06-10
Thank you.

---

### Post by MARP1961 on 2013-06-17
> **deadflowr said:**
> Info bump for you.

I found two bugs on the issue

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1165939](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1165939)

And this one, which contains more commenting, which might help

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1163886](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1163886)

Don't know how helpful it will be, but it's something.

The instructions in the second link work perfectly for me. Software Center no longer opening then closing immediately.

---

