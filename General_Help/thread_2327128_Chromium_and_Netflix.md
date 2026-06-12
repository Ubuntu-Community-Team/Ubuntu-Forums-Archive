---
title: "Chromium and Netflix"
date: 2016-06-07
forum: General Help
---

### Post by rdragonrydr on 2016-06-07
Hello. I am attempting to watch netflix from Chromium, as I do not wish to use Chrome (I can as a last resort... but...). about://plugins shows widevine CDM, and I installed some nss packages.

When visiting Netflix, it tells me to install Silverlight. I suspect that all the things I need are present, but am not certain, and for some reason Netflix will not even try to use HTML 5.

Can you help me with the following:

Do I need to tinker with the user agent so that Netflix thinks I am using Chrome, not Chromium? (If so, how do I do this? I've heard there's a --user-agent=" " argument for running Chromium for command line? Is it correct?)

How do I get Chromium working with NSS or whatever is needed? I am getting conflicting messages here. Some say it can't be done, some say it can, but I can't seem to find a checklist for this. Can I have some detailed instructions please?

THANK YOU THANK YOU THANK YOU!

---

### Post by carl4926 on 2016-06-08
I don't use Netflix but I understand some people actually use Firefox for Windows in Wine with the Windows flash player for FF

---

### Post by rdragonrydr on 2016-06-08
Netflix has stopped using Flash entirely. It either uses Silverlight or HTML5. There's a bunch of stuff out there that talks about how Netflix works with linux autmagically if you install Chrome. Chrome is about the same as Chromium, but Chromium is open-source. It also may have some issues with Widevine, but Ubuntu may have fixed them for its build. I can't tell if it works or not, since my Netflix is apparently not even trying to use HTML5.

Note: My chromium version (in the about page) says it is 50.something. It seems to be newer than most common versions, and this is because of Ubuntu for some reason (It says in the package page that this is the version as well).

---

### Post by raptir on 2016-06-08
> **rdragonrydr said:**
> Netflix has stopped using Flash entirely. It either uses Silverlight or HTML5. There's a bunch of stuff out there that talks about how Netflix works with linux autmagically if you install Chrome. Chrome is about the same as Chromium, but Chromium is open-source. It also may have some issues with Widevine, but Ubuntu may have fixed them for its build. I can't tell if it works or not, since my Netflix is apparently not even trying to use HTML5.

**Note: My chromium version (in the about page) says it is 50.something.** It seems to be newer than most common versions, and this is because of Ubuntu for some reason (It says in the package page that this is the version as well).

Well, current chromium is 53, so that's not a particularly new build.

There are two factors to this. First, as you mentioned, is that Chromium is not intended to work with WidevineCDM. I know that someone made a build for Arch that supports Widevine, but I honestly do not know if the Ubuntu package has proper support for it. Just because it's in your plugins doesn't mean it's actually working correctly.

The other aspect could be that Netflix is expecting only Chrome to support the HTML5 DRM (since Chromium built from source with no modifications does not support it) and will only try to use it if your browser is Chrome. To test that you could change your useragent to Chrome and see if it works. Now, if it *doesn't* work, and still asks for Silverlight, that doesn't necessarily mean that Netflix is not checking for the HTML5 video support. Netflix doesn't throw an error message if your browser does not properly support the HTML5 DRM. The possible paths are:

Test HTML5 -> HTML5 works -> Play video
Test HTML5 -> HTML5 doesn't work -> Test Silverlight -> Silverlight works -> Play Video
Test HTML5 -> HTML5 doesn't work -> Test Silverlight -> Silverlight doesn't work -> Error message to install silverlight

---

### Post by rdragonrydr on 2016-06-08
How can I switch the user agent to Chrome to tes this? I believe I know the command, but I don't know the agent. Otherwise, how can I tell if Widevine works?

I suspected that the Silverlight is a fallback, but I am not certain what to do about it. I hope the user agent will help. If not, does anyone know how to recompile to work with Widevine?

---

### Post by QDR06VV9 on 2016-06-08
Just passing through but have a look here: [https://disqus.com/home/discussion/webupd8/how_to_enable_html5_playback_for_netflix_on_ubuntu_1404_or_1410/](https://disqus.com/home/discussion/webupd8/how_to_enable_html5_playback_for_netflix_on_ubuntu_1404_or_1410/)
And more Here: [http://www.webupd8.org/2014/09/nss-updated-to-allow-native-html5.html](http://www.webupd8.org/2014/09/nss-updated-to-allow-native-html5.html)

---

### Post by SeijiSensei on 2016-06-08
As far as I know, Chromium cannot support Netflix because it doesn't include the DRM features in Chrome itself.

I watch Netflix using Firefox with [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") installed.  You'll also need to spoof your browser's User-Agent string.  For that I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with this string:
```
Mozilla/5.0 (Windows NT 6.1; rv:41.0) Gecko/20131011 Firefox/41.0
```

---

### Post by QDR06VV9 on 2016-06-08
> **SeijiSensei said:**
> As far as I know, Chromium cannot support Netflix because it doesn't include the DRM features in Chrome itself.

I watch Netflix using Firefox with [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") installed.  You'll also need to spoof your browser's User-Agent string.  For that I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with this string:
```
Mozilla/5.0 (Windows NT 6.1; rv:41.0) Gecko/20131011 Firefox/41.0
```

I use Chromium with Netfilx.
But that said SeijiSensei's advice is good also.
Regards

---

### Post by SeijiSensei on 2016-06-08
> **runrickus said:**
> I use Chromium with Netfilx.
I thought the differences between Chromium and Chrome had to do with the proprietary features that couldn't be exposed in the open-source version.  I figured DRM would be high on that list.  But you're right.  I could connect to Netflix and log in without any extra effort using Chromium on my Kubuntu 14.04 system.

I try to stick with Firefox as much as possible, but not having to install pipelight might lead me to Chromium for a few places like Netflix.

After testing, I've found that Chromium doesn't work with Amazon Instant; it tells me to use Chrome.  It doesn't work with Hulu Plus either.  Chromium does work with Flash-based services like Crunchyroll.

---

### Post by rdragonrydr on 2016-06-09
Runrickus, what did you mean that you use Chromium with Netflix? Does that mean you can play videos? If so, can you please tell me how?

I can log in to netflix, but when attempting to play, it fails and wants Silverlight. 

Chromium already has the widevine .so files, so I just need to find out if I need to change my user agent (Say, maybe Netflix blocks non-chrome browsers for HTML5 even if they have all the plugins)? What user-agent string do I need to spoof the latest Google Chrome?

How can I tell if Widevine is working at all, and if not, I've heard about patches to Chromium to allow it to use the plugin, but don't know how to do it. How can I tell if I need to, and how do I do so?


Thanks for your patience.

---

### Post by rdragonrydr on 2016-06-09
One other thing: I went to the bug report about Chromium and Widevine: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274). I was unable to tell if this is fixed yet, but some people have been working on it. I tried Saircot's PPA from there, and that didn't seem to work either, although I have to double check. A fix may have been released to a testing branch of Chromium, though I can't tell for sure and couldn't figure out how to download it to test.

 I am having trouble figuring out the status of this bug!

Has anyone else heard of this who could perhaps tell me what it means, especially the staging PPA? If that really will be released at some point, or works, I would be very interested to know.

---

### Post by courtney2 on 2016-08-08
Bump, if anyone has figured this out. I see the Widevine CDM plugin in Chromium 51, but I can't get Netflix to work. Still tries to get me to install Silverlight

---

### Post by rdragonrydr on 2017-07-11
Well, it's fixed in Ubuntu now for version 54+. Supposedly. I have not had a chance to try yet, but signs seem to say you can move the plugins from the Chrome package into the /usr/lib/chromium-browser directory and it will work...

I hear Firefox caved to the depravity of the movie studio and supports WideVine as well for Netflix. I do not know how to install that; it might be plug'n'play.

---

