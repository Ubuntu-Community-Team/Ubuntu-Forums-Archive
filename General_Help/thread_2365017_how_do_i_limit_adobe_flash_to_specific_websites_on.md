---
title: "how do i limit adobe flash to specific websites on Firefox?"
date: 2017-07-01
forum: General Help
---

### Post by ardouronerous on 2017-07-01
I'm maintaining my dad's laptop which has Lubuntu 16.04 on it, and he tends to play games on Facebook which uses Adobe Flash Player, so for security reasons, I'd like to limit Adobe Flash Player only to run on Facebook and not on the rest of the Internet.

How do I go about doing this?

---

### Post by SeijiSensei on 2017-07-01
I don't think that's possible.  In Firefox you can set Flash to Ask before activating, then tell your dad only to say yes for Facebook.

Frankly I don't think this is a very serious problem.  Does your dad visit lots of wonky sites?  Porn?  Most legitimate sites that use Flash aren't a threat.  Just make sure that you have automatic updates turned on so that Flash is kept up to date.

---

### Post by monkeybrain20122 on 2017-07-01
On Firefox you can just go to tools > Addons > plugins and set flash to 'ask to activate" and tell your dad not to activate it except on Facebook.

More deviously, you can use Chrome to create "webapps" for facebook. Go to facebook from Chrome. Go to the three dots on the upper right corner to get the menu, click more tools > add to desktop then check the box "open as window".This will create desktop files which you can either leave on the desktop or move to ~/.local/share/applications so that an launcher icon would appear in the menu/dash. When click you will go to facebook and nowhere else. 

Then you can hide chrome from your dad by renaming it .desktop file (but have to do it again when there is a chrome update) remove adobe-flash form synaptic and tell your dad to use only Firefox for web browsing and use the "facebook app" (which is an instance of Chrome) for games. But seems like too much troubles.

---

### Post by ajgreeny on 2017-07-01
There is also still a firefox add-on available called flash-block which shows a **Play** icon in all flash windows which I use rather than the firefox plugin activation setting.
It, or something similar is also available for chromium I think.
See [https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss)

This has a white list system to which you can add the facebook website which means flash will work without the need to click the Play icon.

---

### Post by ardouronerous on 2017-07-01
> **monkeybrain20122 said:**
> On Firefox you can just go to tools > Addons > plugins and set flash to 'ask to activate" and tell your dad not to activate it except on Facebook.

My dad's a senior citizen, so he won't know how or what to do.

> **monkeybrain20122 said:**
> More deviously, you can use Chrome to create "webapps" for facebook. Go to facebook from Chrome. Go to the three dots on the upper right corner to get the menu, click more tools > add to desktop then check the box "open as window".This will create desktop files which you can either leave on the desktop or move to ~/.local/share/applications so that an launcher icon would appear in the menu/dash. When click you will go to facebook and nowhere else.

Then you can hide chrome from your dad by renaming it .desktop file (but have to do it again when there is a chrome update) remove adobe-flash form synaptic and tell your dad to use only Firefox for web browsing and use the "facebook app" (which is an instance of Chrome) for games. But seems like too much troubles.

He doesn't like Chrome so he'll know it's Chrome because of the nonfunctional fullscreen Chrome has, unlike Firefox, Chrome's fullscreen doesn't allow navigation inside fullscreen and since my dad's eyesight is poor, he'll have a hard time pressing F11.

> **ajgreeny said:**
> There is also still a firefox add-on available called flash-block which shows a Play icon in all flash windows which I use rather than the firefox plugin activation setting.
It, or something similar is also available for chromium I think.
See [https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss)

This has a white list system to which you can add the facebook website which means flash will work without the need to click the Play icon.

Thanks, I'll give it a try. :)

---

### Post by monkeybrain20122 on 2017-07-02
> **ardouronerous said:**
> My dad's a senior citizen, so he won't know how or what to do.

He doesn't have to do anything. You set it for him. Then go to Facebook, it will ask you to allow flash, then click allow and remember, that's it. You have to do exactly the same with ajgreeny's flashblock addon. In fact the function of flashblock is incorporated into Firefox itself so it is no longer needed.


> 
He doesn't like Chrome so he'll know it's Chrome because of the nonfunctional fullscreen Chrome has, unlike Firefox, Chrome's fullscreen doesn't allow navigation inside fullscreen and since my dad's eyesight is poor, he'll have a hard time pressing F11.


Huh? that is new to me.  Chrome's fullscreen works just fine here. Are you sure it is Chrome rather than Chromium?

This is the new google earth (screenshot) Can you tell it is actually Chrome? I can't (remember to check the open as window option)

---

### Post by ardouronerous on 2017-07-02
> **monkeybrain20122 said:**
> He doesn't have to do anything. You set it for him. Then go to Facebook, it will ask you to allow flash, then click allow and remember, that's it. You have to do exactly the same with ajgreeny's flashblock addon. In fact the function of flashblock is incorporated into Firefox itself so it is no longer needed.




Huh? that is new to me.  Chrome's fullscreen works just fine here. Are you sure it is Chrome rather than Chromium?

This is the new google earth (screenshot) Can you tell it is actually Chrome? I can't (remember to check the open as window option)


Can you get the address bar visible in Chrome's fullscreen like Firefox now? Because based off me and my dad's experience, you can't.

Here's the bug report, a lot of users are requesting this feature, but Chrome said they won't fix it.

[https://bugs.chromium.org/p/chromium/issues/detail?id=8022](https://bugs.chromium.org/p/chromium/issues/detail?id=8022)

---

### Post by monkeybrain20122 on 2017-07-02
Do you mean the menu bar? Well in Unity there is always a menu bar (in System > Appearance choose use system title bar and borders), otherwise the navigation menu is at the 3 dots at the right top corner

But the whole point of creating a webapp, if I understand your purpose correctly, is to prevent him from using it as a browser, so that would be special facebook apps for his games. He doesn't navigate to other sites.


P.S. I don't know how old your father is, but senior citizens are not idiots, just saying. :) My dad is 75 and is not a technical person. He got a smart phone and figured out most things on his own.

---

### Post by ardouronerous on 2017-07-02
> **monkeybrain20122 said:**
> P.S. I don't know how old your father is, but senior citizens are not idiots, just saying. :smile: My dad is 75 and is not a technical person. He got a smart phone and figured out most things on his own.

I know that, based off my conversations with SeijiSensei, he is a senior citizen and he's no idiot :) my brother bought my dad a smartphone two years ago and my dad never figured it out, he still needed me to help him with it.

> **monkeybrain20122 said:**
> Do you mean the menu bar? Well in Unity there is always a menu bar (in System > Appearance choose use system title bar and borders), otherwise the navigation menu is at the 3 dots at the right top corner

But the whole point of creating a webapp, if I understand your purpose correctly, is to prevent him from using it as a browser, so that would be special facebook apps for his games. He doesn't navigate to other sites.

Actually, preventing him from browsing isn't my purpose, because Facebook's news feed leads to other sites on the Internet and that will cause him to leave Facebook.

---

### Post by monkeybrain20122 on 2017-07-02
> **ardouronerous said:**
> 


Actually, preventing him from browsing isn't my purpose, because Facebook's news feed leads to other sites on the Internet and that will cause him to leave Facebook.


Yes, I know that. But he doesn't need flash for facebook, only some games. Correct? Is it possible to create web apps just for those game sites that require flash so that they would appear to be different "desktop games" while using Firefox for other facebook activities?

---

### Post by ardouronerous on 2017-07-02
Actually the games uses Facebook as a platform, he never leaves Facebook when playing the games.

I've found a solution while Googling the problem: NoScript.

I feel NoScript is a better security for my Firefox browser.

[https://www.technorms.com/37427/disable-flash-for-specific-websites-in-chrome-firefox](https://www.technorms.com/37427/disable-flash-for-specific-websites-in-chrome-firefox)
**Setting up site Flash permissions in Firefox**

For avid Firefox-users, setting up site-specific permissions for Flash is also possible. To set these up, the best way to do so is by using the Firefox extension, NoScript. This extension will let you create a “Whitelist” exemption list for the sites allowed to run Flash and other scripts. All other sites not added to this list will be blocked from using Flash.

To setup NoScript, go to the [Firefox add-on page for NoScript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") and click “Add to Firefox”.

NoScript will be added automatically and a restart of the browser is  required. After Firefox restarts, you can add sites to NoScript by going  to “**Add-ons”** in the main menu of Firefox. After finding NoScript, click “**Options**” in the entry for NoScript.


[IMG]https://cds.technorms.com/assets/six49.png[/IMG]


Next, the dialog box for “**NoScript Options**” will load. Make sure to click the “**Whitelist**”  tab. This is the area where you can add URLs of the sites you would  like to give permission to use Flash. After adding a site, make sure to  click “**Allow**” and then “**Ok**.”


[IMG]https://cds.technorms.com/assets/seven41.png[/IMG]

---

### Post by monkeybrain20122 on 2017-07-03
Actually no scripts is an overkill, it blocks all scripts by default so your dad is going to find that images don't load and links won't work on many sites unless he gives permissions to or you have put the site explicitly in the white list It is a lot easier to just set flash to Ask to Activate in Firefox, when it pops up he just needs to click allow and remember once.

---

### Post by ardouronerous on 2017-07-03
> **monkeybrain20122 said:**
> Actually no scripts is an overkill, it blocks all scripts by default so your dad is going to find that images don't load and links won't work on many sites unless he gives permissions to or you have put the site explicitly in the white list It is a lot easier to just set flash to Ask to Activate in Firefox, when it pops up he just needs to click allow and remember once.

Does Ask to Activate ->Allow-> Remember work in incognito mode? My dad values his privacy and has me set Firefox not to remember history.

---

### Post by monkeybrain20122 on 2017-07-03
> **ardouronerous said:**
> Does Ask to Activate ->Allow-> Remember work in incognito mode? My dad values his privacy and has me set Firefox not to remember history.

I don't know, you can check it yourself. But if it doesn't remember that it won't remember your noscripts history either unless you whitelist the site. But since dad is secretive, he probably doesn't want those sites appear in his whitelist either. :)

---

### Post by &amp;KyT$0P# on 2017-07-03
> **ardouronerous said:**
> I've found a solution while Googling the problem: NoScript.
That's like using a supercomputer's command line interface to solve the equation "1 + 1 = x" for x.

You seem somewhat concerned about your dad's technical level.  In addition to what monkeybrain20122 said, note that NoScript is a lot more than a script and plugin blocker.  It also contains many "extra" protections - cross-site scripting (XSS) filter, local network protection, clickjacking protection, HTTPS enforcement, and [more]("https://forums.informaction.com/viewtopic.php?f=10&t=5920").  Unfortunately, quite a few websites are poorly designed in a way that trips the XSS filters.  Someone not well versed in this stuff will need help A) to evaluate how risky each situation is, and B) to allow the specific safe ones.

Also, if I'm remembering right NoScript doesn't save settings changed in private browsing mode.  I can't remember whether there's a setting to disable this behavior.

NoScript is a great addon, great for security, but non-tech users won't want to use it just to block Flash.

---

### Post by ardouronerous on 2017-07-03
> **halogen2 said:**
> That's like using a supercomputer's command line interface to solve the equation "1 + 1 = x" for x.

You seem somewhat concerned about your dad's technical level.  In addition to what monkeybrain20122 said, note that NoScript is a lot more than a script and plugin blocker.  It also contains many "extra" protections - cross-site scripting (XSS) filter, local network protection, clickjacking protection, HTTPS enforcement, and [more]("https://forums.informaction.com/viewtopic.php?f=10&t=5920").  Unfortunately, quite a few websites are poorly designed in a way that trips the XSS filters.  Someone not well versed in this stuff will need help A) to evaluate how risky each situation is, and B) to allow the specific safe ones.

Also, if I'm remembering right NoScript doesn't save settings changed in private browsing mode.  I can't remember whether there's a setting to disable this behavior.

NoScript is a great addon, great for security, but non-tech users won't want to use it just to block Flash.

I've tested NoScript's whitelisting on incognito mode and it works, I've just whitelisted the sites that my dad frequently visits.
And I kinda like NoScript, I have more control of my browser with it, and I read somewhere that NoScript can prevent drive-by downloads.

---

### Post by monkeybrain20122 on 2017-07-03
> **ardouronerous said:**
> I've tested NoScript's whitelisting on incognito mode and it works, I've just whitelisted the sites that my dad frequently visits.
And I kinda like NoScript, I have more control of my browser with it, and I read somewhere that NoScript can prevent drive-by downloads.


It looks like you are looking for something for yourself rather than your dad. I can't see how using NoScript would be simpler for a non  technical person than just click allow and remember once.  Also if your dad is as technically ignorant as you make him out to be I doubt that he would go incognito. Anyway if you are actually doing it for yourself I think YesScript is better than NoScript. It works like NoScript but uses a blacklist instead of a whitelist. Also I found out sometimes ago that you cannot cleanly remove NoScript. It has messed up some of my settings irreversibly, or at least it didn't reverse it when removed (had something to do with playing html5 videos if I remember correctly) Maybe it was because of the presence of other addons, or maybe it was a bug and they have fixed it, I don't know, but I had to restart with a clean profile.

---

### Post by SeijiSensei on 2017-07-03
> **ardouronerous said:**
> I know that, based off my conversations with SeijiSensei, he is a senior citizen and he's no idiot :) 
Thanks, I guess!

I used NoScript for about a day or two before I decided it required way too much manual configuration.  I use Ghostery instead, but I don't think that will help for your problem.

---

### Post by &amp;KyT$0P# on 2017-07-03
> **monkeybrain20122 said:**
>  uses a blacklist instead of a whitelist
... which, for what it's worth, can be achieved in NoScript by setting "Allow Scripts Globally" and marking sites as untrusted.

---

### Post by ardouronerous on 2017-07-04
> **SeijiSensei said:**
> Thanks, I guess!

No problem :D

> **monkeybrain20122 said:**
> It looks like you are looking for  something for yourself rather than your dad. I can't see how using  NoScript would be simpler for a non  technical person than just click  allow and remember once.  Also if your dad is as technically ignorant as  you make him out to be I doubt that he would go incognito. Anyway if  you are actually doing it for yourself I think YesScript is better than  NoScript. It works like NoScript but uses a blacklist instead of a  whitelist. Also I found out sometimes ago that you cannot cleanly remove  NoScript. It has messed up some of my settings irreversibly, or at  least it didn't reverse it when removed (had something to do with  playing html5 videos if I remember correctly) Maybe it was because of  the presence of other addons, or maybe it was a bug and they have fixed  it, I don't know, but I had to restart with a clean profile.

Since I'm maintaining my Xubuntu desktop and my dad's Lubuntu laptop, I usually research security for both systems.

On my dad using incognito mode, I introduced that to him, I taught him all about protecting your privacy online, because when he first started using Facebook, he revealed our entire home address in his profile and I set him straight about that, well me and his friends on Facebook lol.

On NoScript having no whitelist, they do have a whitelist:
[IMG]https://cds.technorms.com/assets/seven41.png[/IMG]

---

