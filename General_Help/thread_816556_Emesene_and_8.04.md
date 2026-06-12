---
title: "Emesene and 8.04"
date: 2008-06-02
forum: General Help
---

### Post by cledus on 2008-06-02
I tried various IM.
I like emesene. and it use to work.
now i get the following. 

Fatal error
This is a bug. Please report it at: [http://www.emesene.org](http://www.emesene.org)

Traceback (most recent call last):

  File "/usr/share/emesene/emesenelib/core.py", line 429, in do_login_successful
    for i in self.contactManager.getADL():

  File "/usr/share/emesene/emesenelib/ContactData.py", line 481, in getADL
    return self.buildDL(contacts, initial=True)

  File "/usr/share/emesene/emesenelib/ContactData.py", line 491, in buildDL
    (user, domain) = i.split('@')

ValueError: need more than 1 value to unpack

and 

Fatal error
This is a bug. Please report it at: [http://www.emesene.org](http://www.emesene.org)

Traceback (most recent call last):

  File "/usr/share/emesene/emesenelib/core.py", line 596, in process
    self.processCommand(command, tid, params)

  File "/usr/share/emesene/emesenelib/core.py", line 605, in processCommand
    self.callbacks.challenge(self, command, tid, params)

AttributeError: 'NoneType' object has no attribute 'challenge'

Can anyone help I am new to this.

---

