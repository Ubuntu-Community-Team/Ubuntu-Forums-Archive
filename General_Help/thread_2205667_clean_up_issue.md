---
title: "clean up issue"
date: 2014-02-15
forum: General Help
---

### Post by Frank_Callo on 2014-02-15
Hi folks.  I am running ubuntu 12.4 on a toshiba satalite laptop (don't remember the satalite model since the stickers all peeled off but its about 28x years old.  

Anyway, we put ubuntu on it after trying, and failing, to reinstall windows.  I put Bleach Bit on here to do cleanup ops and after each time I run it (about twice a eek) I get a number of messages in red, here is an example:

[Errno 13] Permission denied: '/usr/share/espeak-data/fr_dict'

Bleach Bit is telling me that I have only 789 MB of hard disk space and each time I run it I get more of these kinds of messages.  Last nights run yielded nearly a full page of such "error messages" and lots of other red highlighted items beside.  Any ideas?  Is this something to worry about?  Is this something I can remedy?  Any feedback would be greatly appriciated.

---

### Post by mörgæs on 2014-02-15
Normally there's no need for cleaning up a Buntu installation. It's not like Windows where the registry gets full of cruft over time.

```
sudo apt-get autoremove
``` once in a while should be enough.

If you forget about Bleacbit and cleaning are you able to get an installation working?

---

### Post by sudodus on 2014-02-15
Mörgæs is right, It's not like Windows where the registry gets full of cruft over time. But you can still benefit from doing some housecleaning with the Ubuntu Tweak janitor. See this link.

[http://askubuntu.com/questions/75454/how-do-i-install-ubuntu-tweak](http://askubuntu.com/questions/75454/how-do-i-install-ubuntu-tweak)

             Install like this:
  Open the terminal. Add the required repository with the command:
  ```
sudo add-apt-repository ppa:tualatrix/ppa
```
  Update  the software list with the command:
  ```
sudo apt-get update
```
  Finally, install Ubuntu Tweak with the command:
  ```
sudo apt-get install ubuntu-tweak
```
  After that, run it from the menu, or a terminal window or dash typing "ubuntu-tweak" depending on your flavour of Ubuntu and your preferences.

---

