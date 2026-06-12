---
title: "new ubuntu user love it but ...."
date: 2006-12-12
forum: General Help
---

### Post by beldugo on 2006-12-12
why is it so hard  to install a single program? why do i have to go on a mission to find help >_<.. geez. yesterday i had to erase my whole ubuntu installation because of a dumb error.](*,) [-( 

and now im back at another problem.. how do download/install wmv, .mov and etc... codecs.. i cant seem to find a website that can help me on this in some quick steps. 

if anyone have their own website that can help a newbie out let me know please.. and thanks!!

---

### Post by aysiu on 2006-12-12
This has some steps for that:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If that seems like too many steps for you, you should consider using Automatix, which... automates the process for you:
[http://www.getautomatix.com](http://www.getautomatix.com)

And if you don't like the fact that these codecs don't come installed already, you should use another distro like Linspire or PCLinuxOS or Blag. Those have the codecs already installed by default.

And, it's not that hard to install a single program. It's quite easy actually. Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by SuperMike on 2006-12-12
> **beldugo said:**
> why is it so hard  to install a single program? why do i have to go on a mission to find help >_<.. geez. yesterday i had to erase my whole ubuntu installation because of a dumb error.](*,) [-( 

and now im back at another problem.. how do download/install wmv, .mov and etc... codecs.. i cant seem to find a website that can help me on this in some quick steps. 

if anyone have their own website that can help a newbie out let me know please.. and thanks!!

For most newbies, Ubuntu makes it easy to install new software by going into System, Administration, Synaptic Package Manager. (There's also an Add/Remove Programs tool, but I like this one better.) Once there, enable the Universe option to see a whole bevy of software. Do this by choosing Settings, Repositories, Settings, Show Disabled Software Sources, scroll down and place a checkmark on the one that has the word "universe" in it, click OK, and then either choose a package category on the left or use the Search functionality to find something. When you click on a package choice, it gives you a description of it.

Now, put checkmarks in packages you want and then click Apply. It will install these packages and iron out all the dependencies.

But wait! Now that you have done this, don't forget to uncheck the "universe" option in your settings so that the next time your system updates it won't pull from the "community-tested" (rather than Ubuntu-tested) area. To me, the community-tested updates are less stable than the Ubuntu-tested ones.

Close Synaptic and you will likely see the new program in /usr/bin, /usr/sbin, /bin, /sbin, or on your menus.

Now, as for those media formats you spoke about, these are proprietary formats. That's not well-liked in the pure-blooded GNU/Linux community because it means that there's an overly restrictive license and financial cost associated with it. It's also got a format that only vendors who license this format are entitled to build tools for. Instead, the GNU/Linux community would love to see the world seeing the free, open source versions of these sorts of formats, although that hasn't really taken a hold that much.

Automatix is the tool you can install (search this forum for that) to add support for these new media formats, if you absolutely must have them. However, this tool is not officially Ubuntu-supported. Use at your own risk.

---

