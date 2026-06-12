---
title: "While saving a file, cursor not at name option"
date: 2016-11-30
forum: General Help
---

### Post by meetdilip on 2016-11-30
I have been facing this issue since some time. When I try to save a file, select folder to save, I go on type the name. But, instead of the name getting typed, the folder listing jumps to the first letter of the name. ie, if I try to save a file with name iPhone, instead of iPhone getting typed at the name area, the folder content starting with " i " is getting displayed. 

This issue is intermittent. ie, it works fine at times. Is it a bug ? Can you do something related to this ?

PS : Using 16.04 + Unity + latest updates

---

### Post by DuckHook on 2016-11-30
You mention "saving a file" without mentioning the attendant app you are using. Is it nautilus, or a text editor, or rhythmbox, or libreoffice, or something else? Do you have auto-raise focus activated in mouse settings? If so, then the times it works fine may simply be due to having the mouse cursor in your dialogue box, whereas the times it doesn't is because the cursor is hovering over the main app window instead.

---

### Post by meetdilip on 2016-11-30
I often face this issue when saving images from Firefox. I have not done anything with mouse settings ( as far as I can remember ). Let me know if you need any other details. Thanks.

---

### Post by DuckHook on 2016-11-30
Does it happen only in FF? Nowhere else? If so, please have a look at the following mozilla link: [http://kb.mozillazine.org/Changing_media_handling_behaviour](http://kb.mozillazine.org/Changing_media_handling_behaviour)

…especially the part under the heading "Resetting download actions". For convenience, I reproduce the instructions as follows:

[LIST=1]
[*]Type [about:config]("http://kb.mozillazine.org/About:config") into the address bar.
[*]Find the preference **browser.download.pluginOverrideTypes** and, if it is present, right-click on it and select reset.
[*]Find the preference **plugin.disable_full_page_plugin_for_types** and, if it is present, right-click on it and select reset.
[*]Open the [profile folder]("http://kb.mozillazine.org/Profile_folder"). (The profile folder is hidden by default in Windows 7/Vista/XP/2000 and Linux; read [this]("http://kb.mozillazine.org/Show_hidden_files_and_folders") for help finding it).
[*]Note: [In Firefox 3.6 and above you can open the profile folder from the Firefox menu, via "Help -> Troubleshooting Information"]("http://kb.mozillazine.org/Profile_folder_-_Firefox#Using_the_Help_menu_-_Firefox_3.6_and_above").
[*][Completely close your Mozilla browser]("http://kb.mozillazine.org/Kill_application").
[*]Delete (or rename) the file [mimeTypes.rdf]("http://kb.mozillazine.org/MimeTypes.rdf").
[/LIST]
Tell us if this fixes things.

---

### Post by meetdilip on 2016-12-01
To be frank, I do not remember whether it happened while saving from some other app or not
> 

[LIST=1]
[*]Type [about:config]("http://kb.mozillazine.org/About%3Cb%3E%3C/b%3E:config") into the address bar. 
[*]Find the preference **browser.download.pluginOverrideTypes** and, if it is present, right-click on it and select reset. 
[*]Find the preference **plugin.disable_full_page_plugin_for_types** and, if it is present, right-click on it and select reset. 
[*]Open the [profile folder]("http://kb.mozillazine.org/Profile_folder"). (The profile folder is hidden by default in Windows 7/Vista/XP/2000 and Linux; read [this]("http://kb.mozillazine.org/Show_hidden_files_and_folders") for help finding it). 
[*]Note: [In Firefox 3.6 and above you can open the profile folder from the Firefox menu, via "Help -> Troubleshooting Information"]("http://kb.mozillazine.org/Profile_folder_-_Firefox#Using_the_Help_menu_-_Firefox_3.6_and_above"). 
[*][Completely close your Mozilla browser]("http://kb.mozillazine.org/Kill_application"). 
[*]Delete (or rename) the file [mimeTypes.rdf]("http://kb.mozillazine.org/MimeTypes.rdf"). 
[/LIST]


I did exactly as this. There was no **browser.download.pluginOverrideTypes** . As the last step, I deleted mimeTypes.rdf

After than when I tried save an image from Firefox, it worked fine. I will keep you posted on this. Thank you.

Update :

It happened again with Firefox. Could this be a Nautilus bug ?

---

### Post by DuckHook on 2016-12-01
> **meetdilip said:**
> &#8230;It happened again with Firefox. Could this be a Nautilus bug ?It could be anything at all. Did you move the mouse pointer outside the "save" dialogue box while typing? Did the dialogue box have the focus?

Also,
[LIST=1]
[*]list all extensions and plugins you have added to FF.
[*]Are you running standard FF that was part of standard install or did you install a PPA version?
[*]Please provide FF version.
[/LIST]

---

### Post by meetdilip on 2016-12-01
I simply used " Save image as " option and tried to type the file name ( which didn't work )

1. I took a screen shot of add on page

[IMG]http://i64.tinypic.com/22wli.jpg[/IMG]

2. Firefox that came with Ubuntu 14.04 ( I am on 16.04 now )

3. 50.0

Thanks.

---

### Post by DuckHook on 2016-12-01
> **DuckHook said:**
> Did you move the mouse pointer outside the "save" dialogue box while typing? Did the dialogue box have the focus?

> **meetdilip said:**
> I simply used " Save image as " option and tried to type the file name ( which didn't work )Yes, I understand your description of the symptoms, even when you first described them. But I am asking about your mouse pointer when your dialogue box comes up. Please answer my previous questions.

Your screenshot is incomplete and not all add-0ns can be seen. It is impossible to help without full and proper info. In any case, invoke FF in safe mode. This will disable all add-ons. If the behaviour goes away, then the problem is one (or a combination) of your add-ons. Try disabling them one by one until you find out which one is causing the problem. You can Google for how to start FF in safe mode.

Please attach large photos as attachments rather than online images for the sake of those with slow connections or limited data plans.

---

### Post by vasa1 on 2016-12-01
> **DuckHook said:**
> ...
Your screenshot is incomplete and not all add-0ns can be seen. ...
OP, You can click Alt+H > Troubleshooting Information and then click on "copy text to clipboard" near the top of the page. Paste the contents into a text editor and then copy the extensions section (or whatever else) here like this:```
Extensions
----------

Name: Application Update Service Helper
Version: 1.0
Enabled: true
ID: aushelper@mozilla.org

Name: Classic Theme Restorer
Version: 1.5.9
Enabled: true
ID: ClassicThemeRestorer@ArisT2Noia4dev

Name: Greasemonkey
Version: 3.9
Enabled: true
ID: {e4a8a97b-f2ed-450b-b12d-ee082ba24781}

Name: Multi-process staged rollout
Version: 1.5
Enabled: true
ID: e10srollout@mozilla.org

Name: Pocket
Version: 1.0.5
Enabled: true
ID: firefox@getpocket.com

Name: Stylish
Version: 2.0.7
Enabled: true
ID: {46551EC9-40F0-4e47-8E18-8E5CF550CFB8}

Name: uBlock Origin
Version: 1.10.0
Enabled: true
ID: uBlock0@raymondhill.net

Name: Web Compat
Version: 1.0
Enabled: true
ID: webcompat@mozilla.org


```

And a heads-up about one of your extensions: [https://ubuntuforums.org/showthread.php?t=2342528](https://ubuntuforums.org/showthread.php?t=2342528)

---

### Post by meetdilip on 2016-12-02
@DuckHook

> But I am asking about your mouse pointer when your dialogue box comes up.

I did not move the pointer. So, it will be ok to presume that mouse pointer is at the box where we should enter the name.

> Your screenshot is incomplete and not all add-0ns can be seen.

I used Fireshot to take a screen shot of entire page. I guess, that is all I have as addons.

> **vasa1 said:**
> OP, You can click Alt+H > Troubleshooting Information and then click on "copy text to clipboard" near the top of the page. Paste the contents into a text editor and then copy the extensions section (or whatever else) here like this:```
Extensions
----------

Name: Application Update Service Helper
Version: 1.0
Enabled: true
ID: aushelper@mozilla.org

Name: Classic Theme Restorer
Version: 1.5.9
Enabled: true
ID: ClassicThemeRestorer@ArisT2Noia4dev

Name: Greasemonkey
Version: 3.9
Enabled: true
ID: {e4a8a97b-f2ed-450b-b12d-ee082ba24781}

Name: Multi-process staged rollout
Version: 1.5
Enabled: true
ID: e10srollout@mozilla.org

Name: Pocket
Version: 1.0.5
Enabled: true
ID: firefox@getpocket.com

Name: Stylish
Version: 2.0.7
Enabled: true
ID: {46551EC9-40F0-4e47-8E18-8E5CF550CFB8}

Name: uBlock Origin
Version: 1.10.0
Enabled: true
ID: uBlock0@raymondhill.net

Name: Web Compat
Version: 1.0
Enabled: true
ID: webcompat@mozilla.org


```

And a heads-up about one of your extensions: [https://ubuntuforums.org/showthread.php?t=2342528](https://ubuntuforums.org/showthread.php?t=2342528)

Like this ?

```
Extensions
----------

Name: Adblock Plus
Version: 2.8.2
Enabled: true
ID: {d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}

Name: Application Update Service Helper
Version: 1.0
Enabled: true
ID: aushelper@mozilla.org

Name: FireShot
Version: 0.98.89
Enabled: true
ID: {0b457cAA-602d-484a-8fe7-c1d894a011ba}

Name: FlashGot
Version: 1.5.6.13
Enabled: true
ID: {19503e42-ca3c-4c27-b1e2-9cdb2170ee34}

Name: Multi-process staged rollout
Version: 1.5
Enabled: true
ID: e10srollout@mozilla.org

Name: Pocket
Version: 1.0.5
Enabled: true
ID: firefox@getpocket.com

Name: RightToClick
Version: 2.9.6
Enabled: true
ID: {cd617375-6743-4ee8-bac4-fbf10f35729e}

Name: Ubuntu Modifications
Version: 3.2
Enabled: true
ID: ubufox@ubuntu.com

Name: Valence
Version: 0.3.5
Enabled: true
ID: fxdevtools-adapters@mozilla.org

Name: Web Compat
Version: 1.0
Enabled: true
ID: webcompat@mozilla.org

Name: WOT
Version: 20151208
Enabled: true
ID: {a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}

Name: YouTube Video and Audio Downloader
Version: 0.5.5
Enabled: true
ID: feca4b87-3be4-43da-a1b1-137c24220968@jetpack

Name: ADB Helper
Version: 0.9.0
Enabled: false
ID: adbhelper@mozilla.org

Name: PDF Mage
Version: 1.0.3
Enabled: false
ID: jid1-GeRCnsiDhZiTvA@jetpack

Name: Varnam - Transliteration based input tool for indian languages
Version: 2.3.1-signed.1-signed
Enabled: false
ID: jid1-iufO1SfBv6wvAw@jetpack

Name: XDM Helper
Version: 1.6
Enabled: false
ID: xdmff@xdman.sourceforge.net


```

---

### Post by DuckHook on 2016-12-02
> **meetdilip said:**
> …I did not move the pointer. So, it will be ok to presume that mouse pointer is at the box where we should enter the name…Actually, this is not so. Your mouse pointer stays at the last position it was in when dialogue box was invoked. This is usually top left corner of your screen if you have FF maximized or use global toolbar. However, your save dialogue box can appear anywhere, like middle of your screen. If focus-follows-pointer has been turned on for any reason, after one or two seconds, the focus will be lost from the dialogue box and will instead shift to the window that your mouse pointer is still hovering over. In your case, this would be the original web page, hence your symptoms. This is a common issue with auto-raise focus and focus-follows-mouse settings. I use those settings because I prefer them and, after all these years, even I will still sometimes stumble when the focus shifts out of the window I am working on.

It is not possible to be sure because we simply are not sitting in front of your computer the way you are. Hence, we must rely on your eyes and actions and it is especially important for you to be extra observant. Do not assume that the save box has the focus. Look carefully to see which window has the coloured border that declares possession of the focus. Next course of action would be invoking dialogue box, then moving your mouse back and forth over the box to see if it gains/loses focus. You must let it rest over the various windows for some time because there is a time lag built into auto-focus.

> **vasa1 said:**
> a heads-up about one of your extensions: [https://ubuntuforums.org/showthread.php?t=2342528](https://ubuntuforums.org/showthread.php?t=2342528)Words fail to express my disappointment with WoT at this revelation. I have recommended them in the past, and will be removing it from my own browser immediately.

@OP The reported behaviour of this add-on is unlikely the cause of your own symptoms. Vasa1's alert is important, but is tangential to your current issue.

---

### Post by meetdilip on 2016-12-02
@DuckHook

I just tried " save image as " again. This time, the file save window was in focus and I could type in the name without adjusting the cursor. What should I do now ? I save a few images every day and this bug is really getting irritating. Is there any way to get through ?

PS : I depend a lot on WoT. Any alternative available ? Thanks.

Update :

I tried to save an image again, now. This time, the focused window was the file save window. But it still started sorting the files in folder as per what I typed without inputting the file name. Thought of reporting here.

---

### Post by howefield on 2016-12-02
Just a thought, is this a stock 16.04 installation with Unity or have you installed other desktop environments ?

I can't replicate the issue on a vanilla 16.04 installation but have seen it on 16.10 so wondering if you have installed anything that might have updated the gnome or Unity stack.

---

### Post by meetdilip on 2016-12-02
@howefield

I upgraded from 14.04. I had Gnome and Cinnamon then. If it helps, Unity vanished somewhere during that period. I was in Gnome while upgrading to 16.04. I have removed Gnome and Cinnamon now. Only DE I have now is Unity 7 ( I hope the version is correct ).

---

### Post by howefield on 2016-12-02
Sounds a bit of a Frankenstein mess.

Not seeing much in the way of other members having the same issue or current bugs at launchpad, possibly it is something introduced and peculiar to your setup. I'd probably reinstall afresh with your flavour of choice.

---

### Post by DuckHook on 2016-12-02
> **meetdilip said:**
> I upgraded from 14.04. I had Gnome and Cinnamon then. If it helps, Unity vanished somewhere during that period. I was in Gnome while upgrading to 16.04. I have removed Gnome and Cinnamon now. Only DE I have now is Unity 7 ( I hope the version is correct ).<sigh> This sort of history is important to declare from the outset. As howefield has suggested, it is probably the cause of your issues.

In my experience, it it extremely difficult to remove all vestiges of those other DEs. Many new users who *think* they've removed them have actually only removed the metapackage while the entire DE is still there. Basically, one has to remove every single one of the dozens of apps and components that make up the DE, then adjust some config files changed by the initial installation of those DEs--tasks far beyond most beginners to Linux.
> **meetdilip said:**
> @DuckHook

I just tried " save image as " again. This time, the file save window was in focus and I could type in the name without adjusting the cursor. What should I do now ? I save a few images every day and this bug is really getting irritating. Is there any way to get through ?

Based on your reply to this other thread: [https://ubuntuforums.org/showthread.php?t=2345058&p=13577782#post13577782](https://ubuntuforums.org/showthread.php?t=2345058&p=13577782#post13577782)

you are thinking of reinstalling to solve this other problem too? If so, then it makes little sense wasting further time trying to hunt this problem down. I suggest that you back up all important data and reinstall.

> I depend a lot on WoT. Any alternative available ?None, to my knowledge. WoT is unique in its crowd-based reporting. This also has its downside: many sites get unfairly trashed due to the unprofessional nature of the user base. Academic at this point. I will not use them and will rely on my other security measures instead.
> I tried to save an image again, now. This time, the focused window was the file save window. But it still started sorting the files in folder as per what I typed without inputting the file name.This confirms that it isn't a focus issue and is ever more likely a result of mixed up desktop environments.

I strongly suggest a complete reinstall. And also strongly suggest that you don't add or mix DEs anymore. Last but not least, this incident should be a warning to practice a good backup strategy.

---

### Post by DuckHook on 2016-12-02
Additional thoughts&#8230;

When reinstalling, you may wish to rethink the number of add-ons you install into FF. Bad or conflicting add-ons will sometimes also mess up the focus. The best link I could find is this one: [http://superuser.com/questions/1090673/why-does-the-active-firefox-window-occasionally-lose-focus](http://superuser.com/questions/1090673/why-does-the-active-firefox-window-occasionally-lose-focus)

Generalizing this advice:

It is understandable, when first getting into Linux, to try out a lot of new things. It is, after all, the newest and shiniest toy. But those of us who have been around the block a few times&#8213;and especially so helping out in these forums&#8213;know that complexity is the enemy of stability.

You have installed multiple DEs over your OS, 16 add-ons to FF and who knows how many ppa-s, third-party apps and unknown modules to your system. If you wish to experiment in this way, then don't do so on your production machine. Instead:

[LIST=1]
[*]Spin up a VM,
[*]Dual boot into a "play" OS,
[*]Use a completely separate computer.
[/LIST]
Just my two nickels.

Good luck and Happy Ubuntuing!

---

