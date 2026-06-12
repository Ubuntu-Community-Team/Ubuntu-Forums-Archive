---
title: "Chrome is out of date and can't be updated"
date: 2013-01-02
forum: General Help
---

### Post by HunterDX77M on 2013-01-02
I am using Google Chrome and numerous sites have told me that it is out of date. **I've tried updating through the command line and through the Update Manager, but neither has shown any updates **for the browser. I even went to Google and **manually downloaded and installed the "latest" version** they had, but that was the same version I'm already using.

I am currently running Version 23.0.1271.97. **I have the ppa in the Software Sources** ([http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable)). I am running 12.04 (32-bit).

The following sites have given me a message:
[LIST]
[*]Kindle Cloud App: Refused to open because I "not running  a supported browser" even though Chrome is supported.
[*]Google Drive (Docs): Says I'm running an outdated version of Chrome and some features may not work.
[*]Wordpress: Tells me new features won't work well with this version of Chrome and that I should update.
[/LIST]

Can anyone please help me?

---

### Post by dino99 on 2013-01-02
chrome is not supported here; ask on the related fora

ubuntu have chromium in the repository; you can install it:

sudo apt-get install chromium-browser

---

### Post by imachavel on 2013-01-02
Kind of obvious that those other programs/apps/sites don't support chrome and that's your main issue. I'd say those programs/apps/sites suck but I personally use word press quite a bit :popcorn:

try Firefox and use chrome for everything else

---

### Post by vasa1 on 2013-01-02
You're perfectly welcome to ask whatever you like about Chrome here.

The latest version for Linux is 23.0.1271.97 which is what you have.
Source: [http://googlechromereleases.blogspot.com/2012/12/stable-channel-update.html](http://googlechromereleases.blogspot.com/2012/12/stable-channel-update.html)

> The following sites have given me a message:
Kindle Cloud App: Refused to open because I "not running a supported browser" even though Chrome is supported.
Google Drive (Docs): Says I'm running an outdated version of Chrome and some features may not work.
Wordpress: Tells me new features won't work well with this version of Chrome and that I should update.


Of the three sites, I use Google Drive on a daily basis and do not see the warning you see.

May I suggest you look at the advice relating to Linux here: [Create a new browser user profile]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059")? It's possible that your profile has somehow got corrupted.

Could you be more specific about the Wordpress matter? Do you have trouble viewing Word Press blogs? I just visited wordpress.com. At what point do you get the caution that new features won't work well ...?

Edit: you can also ask for help here: [http://productforums.google.com/forum/#%21categories/chrome/linux](http://productforums.google.com/forum/#%21categories/chrome/linux) if you log in with your Google account.

---

### Post by Frogs Hair on 2013-01-02
Considering one of the sites is a Google service I find this strange, so I have to ask if you use any ad or script blocking extensions ? If not see the last post.

---

### Post by vasa1 on 2013-01-02
> **Frogs Hair said:**
> Considering one of the sites is a Google service I find this strange, so I have to ask if you use any ad or script blocking extensions ? If not see the last post.

^^^ also a very likely possibility. Do try accessing those sites with all extensions disabled (chrome://chrome/extensions/).

---

### Post by vasa1 on 2013-01-02
And just to be sure, could you put up the information you see when you enter chrome://version/ in the address bar and hit enter? Please use code tags for clarity.

---

### Post by HunterDX77M on 2013-01-02
Thanks for all the responses.

> ubuntu have chromium in the repository; you can install it:

I used Chromium a long time ago. I switched to Chrome because of the native PDF viewer.

> Could you be more specific about the Wordpress matter? Do you have trouble viewing Word Press blogs? I just visited wordpress.com. At what point do you get the caution that new features won't work well ...?

It's when you are administrating on the dashboard (after you've logged into my_site_name.wordpress.com/wp-admin).

> Considering one of the sites is a Google service I find this strange, so I have to ask if you use any ad or script blocking extensions ? If not see the last post.

Yes. I am running AdBlock Plus and Adblock.


> 
And just to be sure, could you put up the information you see when you enter chrome://version/ in the address bar and hit enter? Please use code tags for clarity.

```

Google Chrome	23.0.1271.97 (Official Build 171054)
OS	Linux
WebKit	537.11 (@136278)
JavaScript	V8 3.13.7.5
Flash	11.5.31.5
User Agent	Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/6.0.481.0 Safari/534.4
Command Line	 /opt/google/chrome/google-chrome --user-agent=Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/6.0.481.0 Safari/534.4 --flag-switches-begin --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/murshed/.config/google-chrome/Default
Variations	853359fa-186f5907
1d3048f1-9de009d0
cd73da34-cf196cb
6214fa18-9e6dc24d
b03ddc1f-2d9ef0cc
4dcb0cd6-d31c4ca1
9d5bce6-30d7d8ac
fe0a565e-595c7724
f9b252d0-fd526c81
3664a344-be9e69ba
ccee547a-766fa2d
571ffcab-766fa2d
f67325bd-da68de77
75f7fb7e-766fa2d
24dca50e-837c4893
ca65a9fe-91ac3782
d1a7fd3-4c2186eb
9c097cbc-d00c3f8d
3028188e-626278e
2bd5ec9c-275837c2
5a3c10b5-e1cc0f14
244ca1ac-4ad60575
246fb659-4c073154
f296190c-e1cc0f14
4442aae2-e1cc0f14
75f0f0a0-4ad60575
e2b18481-e1cc0f14
e7e71889-e1cc0f14
980cfc4b-c5cc9a0a

```

---

### Post by HunterDX77M on 2013-01-02
Here's a screenshot from Google Drive and the Kindle App.

**UPDATE**: I created a new user profile and it seemed to solve the problems. I can now view the Kindle and the Drive isn't giving me any messages. Thanks for your help guys!

---

### Post by AlexDudko on 2013-01-02
> **HunterDX77M said:**
> Thanks for all the responses.



I used Chromium a long time ago. I switched to Chrome because of the native PDF viewer.



It's when you are administrating on the dashboard (after you've logged into my_site_name.wordpress.com/wp-admin).



Yes. I am running AdBlock Plus and Adblock.



```

Google Chrome	23.0.1271.97 (Official Build 171054)
OS	Linux
WebKit	537.11 (@136278)
JavaScript	V8 3.13.7.5
Flash	11.5.31.5
**User Agent	Mozilla/5.0 ([COLOR="Red"]Windows; U; Windows NT 5.2[/COLOR]; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/6.0.481.0 Safari/534.4**
Command Line	 /opt/google/chrome/google-chrome --user-agent=Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/6.0.481.0 Safari/534.4 --flag-switches-begin --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/murshed/.config/google-chrome/Default
Variations	853359fa-186f5907
1d3048f1-9de009d0
cd73da34-cf196cb
6214fa18-9e6dc24d
b03ddc1f-2d9ef0cc
4dcb0cd6-d31c4ca1
9d5bce6-30d7d8ac
fe0a565e-595c7724
f9b252d0-fd526c81
3664a344-be9e69ba
ccee547a-766fa2d
571ffcab-766fa2d
f67325bd-da68de77
75f7fb7e-766fa2d
24dca50e-837c4893
ca65a9fe-91ac3782
d1a7fd3-4c2186eb
9c097cbc-d00c3f8d
3028188e-626278e
2bd5ec9c-275837c2
5a3c10b5-e1cc0f14
244ca1ac-4ad60575
246fb659-4c073154
f296190c-e1cc0f14
4442aae2-e1cc0f14
75f0f0a0-4ad60575
e2b18481-e1cc0f14
e7e71889-e1cc0f14
980cfc4b-c5cc9a0a

```

The problem was in the User Agent line. What did Windows do there?
It should look something like this:
> User Agent      Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11
And Command Line:
> Command Line     /opt/google/chrome/google-chrome --flag-switches-begin --flag-switches-end

---

### Post by HunterDX77M on 2013-01-02
> **AlexDudko said:**
> The problem was in the User Agent line. What did Windows do there?



Yes, I know what it is doing there. I changed the user agent to that so that I could use Outlook mail on premium view. Otherwise, I was forced into basic view, which was annoying to use.

---

### Post by vasa1 on 2013-01-02
> **HunterDX77M said:**
> Yes, I know what it is doing there. I changed the user agent to that so that I could use Outlook mail on premium view. Otherwise, I was forced into basic view, which was annoying to use.

Alex's point is valid. I suggest you keep a second profile that has the modified user agent string and use that to access which ever sites need Chrome 6 for Windows:```
User Agent	Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/534.4 (KHTML, like Gecko) Chrome/**6**.0.481.0 Safari/534.4
```
It's quite bizarre that a site would provide "full service" with Chrome 6 and not Chrome 20-something.

BTW, you mention having both Adblock Plus and Adblock. I hope you don't run into issues on that score as well. I use the first.

---

### Post by HunterDX77M on 2013-01-02
> **vasa1 said:**
> BTW, you mention having both Adblock Plus and Adblock. I hope you don't run into issues on that score as well. I use the first.

No, no issues with them. I have both because ABP was what I used when I used to use Firefox. Chrome's well-known extension was a different Adblock, so I also installed that.

**Thanks again to all.**):P

---

### Post by vasa1 on 2013-01-03
Re. the need for switching the user agent string:> Ever needed to quickly switch between user-agent strings on the fly?  Developing a site that needs to work on both mobile browsers and desktop browsers?  Sick of some archaic site blocking you because you're not using Netscape 4?

The User-Agent Switcher for Chrome is the answer.  With this extension, you can quickly and easily switch between user-agent strings.  Also, you can set up specific URLs that you want to spoof every time.

This version is new and improved, and not only modifies the user-agent sent with the HTTP requests, but also the javascript objects in the page.

Version 1.0.18 updates the manifest version to version 2, and includes some new initial user-agent strings for newer mobile devices.Source: [User-Agent Switcher for Chrome]("https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg/details").

---

### Post by vasa1 on 2013-01-03
> **AlexDudko said:**
> ...
And Command Line:
```
Command Line /opt/google/chrome/google-chrome --flag-switches-begin --flag-switches-end
```

Anyone interested in "fiddling" with the command line can look at [Peter Beverloo's site]("http://peter.sh/experiments/chromium-command-line-switches/")
Taking into account my laptop's age (and specs), mine looks like this:
```

/opt/google/chrome/google-chrome 
  --start-maximized 
  --profile-directory=Default 
  --proxy-server=127.0.0.1:8118 
  --flag-switches-begin 
    --disable-asynchronous-spellchecking 
    --disable-restore-session-state 
    --disable-threaded-animation 
    --disable-webgl 
    --disable-force-compositing-mode 
    --disable-sync-app-notifications 
    --disable-threaded-compositing 
  --flag-switches-end %U
```

(The proxy-server is because I run the Default profile through Privoxy which I use in conjunction with ABP for content "management". I have another vanilla profile for some sites.)

---

