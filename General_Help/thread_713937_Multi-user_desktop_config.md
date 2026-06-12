---
title: "Multi-user desktop config"
date: 2008-03-03
forum: General Help
---

### Post by prop99 on 2008-03-03
Hello

**Background:**
If I want, for instance, a system fan software installed, it is quite easy to find a description on how to do this. 
BUT: Those descriptions are normally based on a desktop computer used by *one* person, meaning that if another person logs in to this machine, the startup scripts and whatever are useless.
Another example is the samba automount. I haven't found *any* description on how to setup samba automounting for any user that logs in to the computer.

**Question:**
I am looking for documentation on how to setup servers and clients that would work in a "corporate environment", with:
[LIST] [*]several users
           [*]centralised authentication
           [*]centralised scripts (and policies)
           [*]centralised backup strategy
           [*]description on how to setup the clients for using these
[/LIST]

Any help in finding these docs (which I am sure exist) would be appreciated, thanks!

  //jan e

---

### Post by Scarath on 2008-03-03
These seem to be along the lines of what you speak, hope they are of use.

[https://help.ubuntu.com/community/MultiseatX]("https://help.ubuntu.com/community/MultiseatX")
[http://www.michaeltinsay.com/?q=Multiseat-Gutsy-Xephyr]("http://www.michaeltinsay.com/?q=Multiseat-Gutsy-Xephyr")
[http://linuxgazette.net/124/smith.html]("http://linuxgazette.net/124/smith.html")
[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html]("http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html")

---

### Post by prop99 on 2008-03-07
Not really what I meant by multi-user.

I meant a computer that can be used by me one day and by someone else the next day.

As I said, most config/setup issues I have seen are resolved by configuring these services (or whatever) _for one user_, the user "owning" this computer.

For the Samba example:

I could modify my etc/fstab file pointing to my personal credentials file. This will make my network connections available when I log in. But what happens if someone else logs in? They will use the same fstab file and MY credentials. 
This is not the way I want to setup my desktop computer. I want it to adapt to whoever logs in, and use the logged-in persons network connections.

So what I want may be this:

[LIST=1]
[*]Setup a static startup behaviour for the computer
Here antivirus program, hardware control apps and other could be started
...
[*]Setup dynamic startup behaviour that depends on whoever just logged in
Typically setting up network connections for the logged-in user.
...
[/LIST]

I hope this makes it clearer...

  //jan e

---

### Post by prop99 on 2008-03-12
Progress:

I found some very good docs on this topic:

[LIST]
[*][Ubuntu 7.10 Small Business Server (version 2.0)]("http://rrcomputerconsulting.com/view.php?article_id=3")
[*][OpenLDAP + Samba == Domain Controller]("http://rrcomputerconsulting.com/view.php?article_id=2")
[/LIST]

The preface of the second doc is quite interesting...

  //jan e

---

