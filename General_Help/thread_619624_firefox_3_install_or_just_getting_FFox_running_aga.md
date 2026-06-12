---
title: "firefox 3 install or just getting FFox running again!"
date: 2007-11-21
forum: General Help
---

### Post by Protagonistics on 2007-11-21
So I got all excited that FFox 3 beta was released. I downloaded the file from web site whose address I cannot recall and which I cannot find in google searches) and ran it. It only extracted the firefox folder set with chrome, profiles, etc. in it. I'm not familiar with what .exe is in linux so I just tried running the scripts in the folder but to no avail. Being unafraid, I simply replaced my old .mozilla folder with the new .mozilla one. Now, every time I start FF, I am told to create a profile. But when I do and hit Create, it gives me an error message stating:

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520005
(NS_ERROR_FILE_DESTINATION_NOT_DIR) [nslToolkitProfileService.createProfile]"  nsresult:
"0x80520005 (NS_ERROR_FILE_DESTINATION_NOT_DIR): location: "JS frame ::
chrome://mozapps/content/profile/create/ProfileWizards.js :: onFinish :: line 233" data:no]

So I hit OK, the only option and go back to create a profile screen. Ok, I'll just put my profile somewhere like the desktop since I think I can't Write in wherever the standard location is. While this allows me to use FF, the NEXT time I open the browser, I have to do it again! I've tried reinstalling FF2 completely from Synaptic but nothing changes! In fact, I NEVER had FF3- ever time I checked the Help>About, it always said the version 2.0.0.8. 

Wow, I messed this one up good. Any ideas?

Thanks!

---

### Post by JAwuku on 2008-03-18
**This post could be related to an Ubuntu bug filed at**: #123917 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having the same problems also, but with a slightly different twist.

I'm running Ubuntu Gutsy 64-bit.

Inside, I'm running a 32-bit chroot which houses 32-bit firefox and swiftfox 3.0. 

The 32-bit firefox was installed automatically from synaptic (version 2.0.0.12), while the swiftfox deb was installed from [www.getswiftfox.com](www.getswiftfox.com).

I get the same errors, and cannot create a profile from either firefox and swiftfox.

> Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520005
(NS_ERROR_FILE_DESTINATION_NOT_DIR) [nslToolkitProfileService.createProfile]" nsresult:
"0x80520005 (NS_ERROR_FILE_DESTINATION_NOT_DIR): location: "JS frame ::
chrome://mozapps/content/profile/create/ProfileWiz ards.js :: onFinish :: line 233" data:no]


Also, outside the chroot, 64-bit firefox 2.0.0.12 refuses to run, saying it can't find the library libxpcom_core.so, which is already installed as part of the firefox package.

i've tried reinstalling firefox, but to no avail.

How do I solve this problem? Any help is appreciated.

Thanks

---

