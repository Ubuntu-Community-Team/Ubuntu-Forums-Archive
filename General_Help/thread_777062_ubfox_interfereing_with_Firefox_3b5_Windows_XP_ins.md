---
title: "ubfox interfereing with Firefox 3b5 Windows XP install"
date: 2008-05-01
forum: General Help
---

### Post by Vilkku on 2008-05-01
I have a bit of a situation going on atm, with my Windows Firefox installation becoming messed up after I upgraded Ubuntu to 8.04. I'll explain step-by-step what I did:

1. Use Firefox 3b5 normally in Windows XP. Everything works.
2. Boot up Ubuntu 7.10, open Firefox 2. I have set it up so that both the Ubuntu and Windows installation are using the same profile folder, for extension sharing. It crossed my mind that it might not have been the best idea to use two different versions of Firefox with the same profile folder, but it didn't seem to cause any problems.
3. Upgrade to 8.04 from within Ubuntu. As you know, that includes Firefox 3b5. Open Firefox 3b5 in Ubuntu, everything works, noticed there is a new extension (ubufox) and that the language is Endlish (using Swedish install). Changed locale to Swedish using the extension manager. Like I said, everything works.
4. Boot into Widows XP again. Open up Firefox 3b5. Noticed all extensions were not working (they are however listed in the extension manager, but without their icons)(dictionaries are working and they also have their icons). Noticed Ubuntu Firefox Modifications was listed as well, and that the English locale was available (didn't have it before)(using Swedish Firefox). Tried a number of different settings (like deactivating the "extra" extensions, removing them etc.) but whenever I restarted Firefox they were all still there and in the same state as before.
5. Started looking around. Checked the Firefox install directory in Windows. Noticed that "langpack-en-GB@firefox-3.0.ubuntu.com", "langpack-sv-SE@firefox-3.0.ubuntu.com" and "ubufox@ubuntu.com" folders under \Mozilla Firefox\extensions (once again, in the Windows XP install directory). All these folders were empty, tried deleting them. Opened Firefox, same issue, and the folders were recreated.
6. Went back to Ubuntu, opened Firefox and all extensions were still working there as you'd expect, and the Extension Manager wasn't behaving strange.
7. Back again in Windows, same issue.

There you go, any help appriciated. If you guys need any more details, just ask right away. Please keep in mind that I'm not experienced at all with Ubuntu, especially anything terminal-related will need explaining ;)

EDIT: Noticed that Firefox works perfectly normal if I created a new profile in Windows. So, problem must be located in the profile folder. Also noticed I misspelled the topic title ><

---

### Post by blakegrover on 2008-05-16
The Ubuntu firefox modification addon probably is causing this conflict, disable this addon in firefox in linux and then reboot into windows and see if this fixes it.  This addon was not made to run under windows.  Also you will need to be careful installing other addons if they say they only work in windows or in linux (Some addons only run in one os).

Blake

---

### Post by blakegrover on 2008-05-16
It looks like it fixed it temporarily and now its going to offline again.  Sorry, but if I find out any more information I'll post it here.

Blake

---

