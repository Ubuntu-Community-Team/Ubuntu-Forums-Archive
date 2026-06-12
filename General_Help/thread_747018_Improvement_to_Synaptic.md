---
title: "Improvement to Synaptic"
date: 2008-04-06
forum: General Help
---

### Post by NawaMan on 2008-04-06
Until today, I like Synaptic so much. It is a great tools and almost never cause problems to me at all. Well ... until today.

I found a problem that is not a bug but rather a needs for improvement. this is what did.

My wife use EEEPC for lot of things including as a media player. It comes with SMPlayer which have a lot of problems (like sound synchronization). I hate it too. So I install VLC for her (don't want to bother with codecs and so on). VLC works but once it encounter problems in the VDO file it stop playing it (not give me a change to skip the problem area). VLC used to be able to handle problems in the media files very well but not anymore and I don't know why. So at the end, I install Totem and gstream-ugly which work very well.

Now here is the problem, since the EEEPC has less storage, so I want to uninstall VLC and other packages that come with it (that will become unused after VLC is gone). But uninstall VLC does not uninstall its depended packages. At the end, I opened the 'History' list and uninstall it one by one (pain in the xxx). I can't just copy the list and append it using 'sudo apt-get remove ...the list here ...', either because some of the packages are used by Totem that I installed after VLC.

Therefore, I want to suggest that what if Synaptic remember that I install VLC as **a main program** and the rest are **dependency**. Then when I want to uninstall a main program (in this case is VLC), it also remove every dependencies of the main program unless the dependencies now being used by other main programs.

In other word, I propose that Synamic should distinguish **'main programs'** and **'dependencies'**. If I install main program - it install all dependencies for me. If I uninstall main program - it uninstall the dependencies for me.

Sure, I can uninstall everything in '(auto removable)' or '(residue config)' but doing this is still useful. It can help simplified package management more because the users can see and manipulate only the main programs and not every single package like those libraries that almost no one know what is it. Like having a simple mode and advance mode in Synaptic.

Defining what packages are main programs can be done by the distro or recognize it from what users choose to install (not the dependence) or whatever appropriate criteria are.

What do you guy think?

---

### Post by ramjet_1953 on 2008-04-06
I think you may find that Synaptic already has the feature that you want.

When you have Synaptic running and you have the package that you want to remove in the main window, just right click on it and a menu will open. One of the options is for complete removal, which removes all of the dependencies for that particular application, providing that they are not required for any other application.

Regards,
Roger :cool:

---

