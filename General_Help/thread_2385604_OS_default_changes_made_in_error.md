---
title: "OS default changes made in error"
date: 2018-02-22
forum: General Help
---

### Post by kimberley2 on 2018-02-22
I an using Firefox 58.0.2 in xubuntu 16.4 and in an endeavour to fix tab crashes on my browser I altered 2 configurations in the default set up and now cannot remember which ones! I need to get back to the set up defaults but do not know how to do this and would appreciate help.  I am not technically proficient so have to have simple instructions. Many thanks

---

### Post by #&amp;thj^% on 2018-02-22
> **kimberley2 said:**
>  I altered 2 configurations in the default set up and now cannot remember which ones! Many thanks
I'm not sure how any of us would know what changes and where they were made??
If you used the terminal to make the changes look for your .bash_history in your Home Directory.
Just not enough information to safely advise you. :)
EDIT: Did you make these changes in Firefox? If so you can follow this to reset Firefox to it's default settings:
**First If it were me, I would just make a copy of your .mozilla folder and keep it safe in another folder.**
If the changes were made to Firefox within Firefox you will be able to reset firefox via:
In the URL or address bar enter this:
```
about:support
```
Now on the left you will see: "Refresh Firefox"
Firefox will close to refresh itself. When finished, a window will list your imported information. Click Finish and Firefox will open. 

**What does the refresh feature do?**

All of your Firefox settings and personal information are stored in a profile folder. The refresh feature works by creating a new profile folder for you while saving your important data.

_Add-ons which are normally stored inside the Firefox profile folder, such as extensions and themes, will be removed. _Add-ons stored in other locations, such as plugins, will not be removed **but any modified preferences (such as plugins you have disabled) will be reset.**
Firefox will save these items:

  >   Bookmarks
    Browsing and download history
    Passwords
    Open windows, tab groups and tabs
    Cookies
    Web form auto-fill information
    Personal dictionary 

**Important: These items and settings will be removed: (Make sure you have back-ups)**

Extensions and themes, website permissions, modified preferences, added search engines, DOM storage, security certificate and device settings, download actions, plugin settings, toolbar customizations, user styles and social features will be removed. 

Note: Your old Firefox profile will be placed on your desktop in a folder named "Old Firefox Data" Not on Linux though. If the resetrefresh didn't fix your problem you can restore some of the information not saved by copying files to the new profile that was created. If you don't need this folder any longer, you should delete it as it contains sensitive information.
So if anything you needed would be in your backed-up .molzilla folder that you should have made.
Or you could simply Create a new fresh profile for firefox via:
```
firefox -P
```

---

### Post by kimberley2 on 2018-02-23
Hi there and thank you so much for your prompt response. I tried the first option which failed and also the second option of a fresh profile for Firefox but unfortunately a few tabs are still crashing, most importantly my online banking. My bank have been involved so I know the problem is not with them. However, my PC was built to specification in France in 2002 and has served me well without anything being replaced since then, so perhaps it is just giving up the ghost! Your advice was much appreciated.

---

