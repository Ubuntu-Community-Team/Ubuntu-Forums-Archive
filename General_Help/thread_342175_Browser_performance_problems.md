---
title: "Browser performance problems"
date: 2007-01-19
forum: General Help
---

### Post by PaulFXH on 2007-01-19
Hi
I've just upgraded to Edgy and most things are going fine although I really, as yet, don't see too much difference from Dapper (but maybe that can be attributed to my inexperience).

Nevertheless, I am seeing some bizarre browser behaviour. Let me explain...........

I have three browsers available: Swiftfox, Firefox 2.0 and Opera 9.10

Swiftfox works very well with rapid start-up and page/link retrieval other than the fact that it insists on checking the compatibility of add-ons every time I launch it. However, as this takes only 1-2 seconds, I can tolerate this.

Firefox, on the other hand seems to toggle the IPV6 DNS Disable switch all by itself with no encouragement from me (as far as I'm aware) leading to very slow performance (1-2 minutes to open a page). In addition, with this switch toggled to False, the first page to show on launch is the Edgy Release notes even though the Home Page is Google. The Google page shows as a second tab with the circling thing showing that it's still loading. This loading however, takes about 2 minutes after which I still need to click the tab to get to what's supposed to be the opening home page.
When the switch is toggled back to True, opening is far quicker (almost as good as Swiftfox) and Google comes up immediately with no mention of the Edgy Release notes. However, the next time I launch, the switch will have been toggled back to False.

The performance of Opera is very reminiscent of that of Firefox in that page retrieval is, in general, very slow at 1-2 minutes. This is so disappointing given that Opera is much vaunted as the fastest browser.
I did have an indication of an error (conflict with installed version of Opera) during installation which I sought to resolve by removing Opera and reinstalling. However, while I was able to uninstall Opera from Windows by locating the uninstall .exe in the Opera folder, I just cannot find this, nor any other means of removing Opera from Ubuntu.

I would appreciate any advice on the following three problem areas:

i) Why does Swiftfox persistently check for Add-On compatibility on launch?

ii) Why is Firefox toggling the IPV6 DNS Disable switch?

iii) How can Opera be removed from Ubuntu given that it doesn't show up in Applications>Add/Remove?

Paul

---

### Post by bollix47 on 2007-01-19
1. type about:config in address line

look for local_install.extensions.checkCompatibility

change it to false.

2.  Have a look [here]("http://ubuntuforums.org/showpost.php?p=2037207&postcount=2").

3.  Opera is not installed by default in edgy or dapper.  How did you install it?

---

### Post by PaulFXH on 2007-01-19
Thanks for the reply bollix47 (that just cannot be your real name!)
I tried both of your suggestions with results as follows:

1. about:config did not display any lines even remotely resembling "llocal_install.extensions.checkCompatibility". The change you suggested was therfore not possible. What does this indicate, if anything?

2. I made the edit change suggested in the "here" link but this made no difference whatsoever to Firefox toggling the IPV6 DNS Disable switch of its own accord.

Incidentally, it appears that it may be Swiftfox which is precipitating this adverse change in Firefox. I found this out by toggling the IPV6 switch back to True and then I launched FF 5-6 times with a couple of Opera launches in between. Every time, FF launched quickly with the IPV6 switch still on True.
However, when I launched Swiftfox, shut it down and re-launched FF, it came back with the IPV6 switch at False.

You asked where I got Opera from. It came from here: [http://www.opera.com/download/](http://www.opera.com/download/)

Paul

---

### Post by bollix47 on 2007-01-19
1.  You show two l's in local.  there's only one.

2.  If you turn off IPV6 in ubuntu it shouldn't matter what the setting in Firefox is.

3.  Since you installed it manually I don't know how you can uninstall it.  Check the folder where you downloaded it and see if there's an uninstall script.  Unlikely but ya never know. :wink:

---

### Post by Sef on 2007-01-19
> You asked where I got Opera from. It came from here: [http://www.opera.com/download/](http://www.opera.com/download/)


It's in multiverse now, so a simple download, once the repositories are open.

---

### Post by PaulFXH on 2007-01-20
Thanks to bollix47 and Sef for the replies.

bollix47:
1. Yes, I made an error but only in writing my last message. Actually, nothing at all showed up in about:config that started with the letter "l".
2. Unfortunately, in my case it didn't seem to make any difference. However, I was able to solve this problem by designating this switch to always stay on True through a user.js file in the Firefox Profiles folder
3. Couldn't find any uninstall file even though I was able to remove Opera from my Windows XP partition by means of a uninstall.exe. Nevertheless, I was able to resolve my Opera problem based on the advice from Sef.

Sef:
That was most useful advice as well as showing me how to REMOVE Opera should I need to again. However, I used Synaptic to install ALL of the packages associated with Opera and, guess what, it works absolutely perfectly now. Even faster than Swiftfox.
What a transformation.

Many thanks for your help, guys
Paul

---

### Post by bollix47 on 2007-01-20
You're welcome.  Glad to see you got it sorted.

1.  Sorry about the confusion.  You would only have that preference if you had [Mr Tech's Local Install]("https://addons.mozilla.org/firefox/421/") extension installed.

---

