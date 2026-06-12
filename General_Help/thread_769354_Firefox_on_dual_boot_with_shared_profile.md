---
title: "Firefox on dual boot with shared profile"
date: 2008-04-26
forum: General Help
---

### Post by dfreidin on 2008-04-26
I have a dual boot with Vista and Hardy (used to be Gutsy). I've got Firefox installed on both, and I've set it up so that the Firefox profile on Linux is a symbolic link to my Firefox profile on Windows. I've had that set up for as long as I've had this dual boot, and it worked fine until maybe a month or two ago, when my addons stopped working in Linux. I would have posted this then, but I've been really busy. Anyway, I know the profile is still working because my bookmarks are fine, and the addons show up in Linux, they just don't do anything. I also share profiles for Thunderbird and Sunbird, and they don't have any problems. I'm not sure what the problem might be. My only guess is that maybe because the Firefox's are different version numbers (even more so when Hardy upgraded to Firefox 3 beta), the addons aren't compatible with both versions. Does that make sense, or is there some other reason that this might be happening?

---

### Post by dfreidin on 2008-04-26
Okay, it's not a version issue (as far as I can tell) because I installed Firefox 3b5 on Vista, and my addons work fine (the ones that are compatible anyway), but now that I'm back into Hardy, the addons aren't working here. They used to work, so I have no idea what the problem is. Can anyone help?

---

### Post by sagesparrow on 2008-05-29
I have the same problem.  The addons work fine in Windows, but not in Feisty which I'm using.  

If I remove the following files from the profile folder (the folder you specified when you created the profile) and restart firefox the addons will work:
extensions.ini
extensions.rdf

The only problem is that these files reestablish themselves with each new start up.  Anyone know how to stop these files from reappearing?

---

### Post by brandjamie on 2008-05-30
hi, i'm having the same problems and then some. 

i'm not sure if i did something stupid but at the moment every time i change to windows and back i get locked out with the .parentlock file - i know i can delete it but it's getting tiresome. 

i guess it's connected with this problem as i'm not getting all the extensions in ubuntu that i have in windows (they say they are installed in the plug in manager but they don't work). 

to add to the weirdness everytime in change operating system and load firefox i get the plugin manager telling me that new plugins have been installed (the plugins have all been installed for a while) AND firefox goes to the 'What's new in firefox 3' welcome page (in the preferences it's set up to show my windows/tabs from the last session). 

well, that's a lot of extra problems but i'll be working on them. anyone figured out how to get the plugins working yet?

---

