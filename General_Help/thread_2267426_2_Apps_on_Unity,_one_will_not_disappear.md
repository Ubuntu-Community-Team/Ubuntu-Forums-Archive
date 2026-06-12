---
title: "2 Apps on Unity, one will not disappear"
date: 2015-03-01
forum: General Help
---

### Post by tom167 on 2015-03-01
I'm kinda new to Ubuntu, so please help me out here.
I downloaded an app from Ubuntu's Software center, thinking all would be arlight.
I didn't want it anymore after awhile, so I uninstalled it.
The only problem is that it install a second app that has no actions, and cannot be launched.
I can't seem to remove it from my app thingy, as I cannot uninstall.
I installed another app and there is a second one that is the same.
Images:
[IMG]http://i.imgur.com/Y7u4nGW.png[/IMG]
[IMG]http://i.imgur.com/cNsAhwz.jpg[/IMG]

Anyway I can remove this?

---

### Post by gifford on 2015-03-01
It is not an app but a document on VLC. Check in your document folder to remove.

---

### Post by tom167 on 2015-03-01
I have nothing in my Documents.

---

### Post by gifford on 2015-03-01
Maybe you can be more specific. Is it the VLC app you want to remove?
And did you attempt to install it again?

---

### Post by tom167 on 2015-03-01
> **gifford said:**
> Maybe you can be more specific. Is it the VLC app you want to remove?
And did you attempt to install it again?
It is VLC, Skype, and MyPaint.
I have 2 icons of MyPaint, and Skype never properly installed.
I did attempt to install VLC again to see if it would remove the second uninstall. This attempt failed.

---

### Post by gifford on 2015-03-01
OK...what version of Ubuntu are you using?
The issue should be easy to correct but do need to know the version you are using.

---

### Post by tom167 on 2015-03-01
I am using 14.04 LTS.

---

### Post by tom167 on 2015-03-02
bump.

---

### Post by gifford on 2015-03-02
Let's start with the easy way. Open the dash and right click mypaint app, you should now get a screen to uninstall. Try it first.
I am not sure from your post how you uninstalled the apps. Did you use the software center or synaptic?
You can also use the command line in the terminal.
I would suggest for VLC that you run this command :sudo apt-get purge VLC
This will remove VLC and associated files.

Also, are you running Ubuntu 14.04.2? Or 14.04? Is this a new install that you downloaded? If so it is probably 14.04.2.
Check in terminal with this command: lsb_release -a

---

### Post by tom167 on 2015-03-02
> **gifford said:**
> Let's start with the easy way. Open the dash and right click mypaint app, you should now get a screen to uninstall. Try it first.
I am not sure from your post how you uninstalled the apps. Did you use the software center or synaptic?
You can also use the command line in the terminal.
I would suggest for VLC that you run this command :sudo apt-get purge VLC
This will remove VLC and associated files.

Also, are you running Ubuntu 14.04.2? Or 14.04? Is this a new install that you downloaded? If so it is probably 14.04.2.
Check in terminal with this command: lsb_release -a
Thank you for trying to help.
I am running 14.04.2.
Using that command, it did nothing to help solve the problem.
I do not want MyPaint gone, I just want the document copy gone.
It seems to make this copy for every application I download from Terminal or the Software Center.
I also uninstalled VLC from right clicking and clicking Uninstall.

---

### Post by tom167 on 2015-03-03
Bump.

---

### Post by tom167 on 2015-03-03
bump.

**Edit:** Sorry, my computer was being stupid and I thought it didn't post.

---

### Post by tom167 on 2015-03-03
bump

---

### Post by tom167 on 2015-03-04
bump

---

### Post by deadflowr on 2015-03-04
Try this:
open the dash and search for privacy, which should show an app called Security and Privacy, and hit enter.
Now when the privacy app opens navigate the tabs to the Files and Applications tab.
Click on the button at the top right area marked clear usage data(or something like that)
Choose From all time. (Since it is unclear when the app first appeared, unless that is something you do know, otherwise set a specific date range)
Hit enter.

Does the app still show for you?

---

### Post by tom167 on 2015-03-04
> **deadflowr said:**
> Try this:
open the dash and search for privacy, which should show an app called Security and Privacy, and hit enter.
Now when the privacy app opens navigate the tabs to the Files and Applications tab.
Click on the button at the top right area marked clear usage data(or something like that)
Choose From all time. (Since it is unclear when the app first appeared, unless that is something you do know, otherwise set a specific date range)
Hit enter.

Does the app still show for you?
Thank you so much.
It bugged the crap out of me.
They don't show up anymore.
I thank you.

---

