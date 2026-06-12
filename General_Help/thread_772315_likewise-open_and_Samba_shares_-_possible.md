---
title: "likewise-open and Samba shares - possible?"
date: 2008-04-28
forum: General Help
---

### Post by kalahari875 on 2008-04-28
**Task:** Join Ubuntu server to the Windows Active Directory domain with likewise-open, and set up Samba shares allowing certain AD groups access.

Is this possible? I was able to get the machine joined to the AD domain successfully via [this article]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/"), and can login with AD domain accounts. I can't figure out how to configure the shares though. I've tried various things and always end up with Kerberos errors and endless prompts to the Windows clients where the shares refuse access.

---

### Post by untjake on 2008-05-28
I'm having the exact same trouble. Did you make any progress? It seems like it should be strait forward to set up samba to authenticate through pam exactly like the logon does.

---

### Post by adwatkin19 on 2008-06-02
I would also like to get in on this, it would seem a useful feature to incorporate into likewise to assist in connecting to SAMBA or windows shares using the login details you give it. 

Just as a notion to this, when you enter domain\username and then your password at the login screen, so we know where this information is kept, as it could be possible to use this information in a script to mount the required shares. 

Anyone know?

Adam

---

### Post by ic3000 on 2008-06-29
Same question here!

This will be a great feature to make it possible to add more linux users on networks that are now only using windows.

Likewise open is a great tool that acomplish alot but still misses the step to connect to the users home folder or documents folder on the windows server.

---

### Post by mem on 2008-07-08
after having done this, i cant say i recommend it.

if you want to try it yourself you need to use the full version of likewise-open from their site. The version in the ubuntu repos does not install all the necessary parts.

if you google around you'll see somewhere on the likewise site that they have a guide to setting up samba 3 with likewise-enterprise. the steps are the same for likewise open.

I spent the last 5 days dealing with this software and when i finally did uninstall it, it nuked all of my config files and i had to go through and manually replace the ones that where backed up upon installation. To save myself the trouble i just reinstalled ubuntu.

i've chosen to go back to the old way of joining a box to an AD. more steps? yes. Yet every time i've done it, i've never had an issue like i did this weekend with likewise.

maybe i'll try it again in 6 months and see if its gotten any better...

---

