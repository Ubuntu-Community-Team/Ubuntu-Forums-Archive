---
title: "Screenlets AppMenu (and others) bug!?"
date: 2008-05-08
forum: General Help
---

### Post by situz on 2008-05-08
Hello! 

I recently heard about this screenlets program, and i wanted it, badly! =)

so I found this how to guide:
[http://linuxtechie.wordpress.com/2008/01/14/how-to-screenlets-bzr/](http://linuxtechie.wordpress.com/2008/01/14/how-to-screenlets-bzr/)
and did what it told me. 

so far so good, I locate the "screenlets" menu on the main menu, and it seems that only few of the screenlets are willing to launch. Some of the one's who do launch are: "sensors" "sysmonitor" (I guess there are more too, but haven't tested that many)

but the AppMenu does not seem to appear for me, so I open the "screenlets" from the terminal: 
> /usr/share/screenlets-manager/screenlets-manager.py > /dev/null

and watch the terminal closelly while I click the Launch/add button on the AppMenu, heres the outcome: 

> Traceback (most recent call last):
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 344, in <module>
    screenlets.session.create_session(AppMenuScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 446, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 237, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 55, in __init__
    uses_theme=True,ask_on_option_override = False,  **keyword_args)
TypeError: __init__() got an unexpected keyword argument 'ask_on_option_override'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_share_screenlets_AppMenu_AppMenuScreenlet.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 344, in <module>
    screenlets.session.create_session(AppMenuScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 446, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 237, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/usr/share/screenlets/AppMenu/AppMenuScreenlet.py", line 55, in __init__
    uses_theme=True,ask_on_option_override = False,  **keyword_args)
TypeError: __init__() got an unexpected keyword argument 'ask_on_option_override'


Anyone have any idea what the problem is? 

I'm running on ubuntu 8.04, with an amd64 x2 cpu and ati radeon x1900xt graphics card. 

Thanks alot in advance for any help! =)

---

### Post by situz on 2008-05-09
well nvm, I installed AWN instead ^^

---

