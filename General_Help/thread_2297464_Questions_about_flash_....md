---
title: "Questions about flash ..."
date: 2015-10-03
forum: General Help
---

### Post by eightbits2010 on 2015-10-03
Using Ubuntu 14.10, and Firefox for a browser.
About three days ago Facebook could not display any videos in post. when I used Chrome, there were no problems with FB videos.
also, the ubuntu PC did not have any video issues with youtube videos.

I also have a netbook type PC that I recently deleted Ubuntu 14.10 on it and installed Xubuntu 14.'04 (clean install). 
With that configurations there were no problems. I did notice that the ISO install had Firefox 41.0 installed and the Ubuntu 14.10 PC had Firefox installed at 39.0.
I could not find a way to attempt to install Firefox 41.0, there is no upgrade in the software center and Synaptic didn't show anything either :eek:.

So, I hope that can assist in understanding if and when a fix is available. I really prefer to use Firefox.

---

### Post by eightbits2010 on 2015-10-03
So, how can the older flash be installed? DO you know why Chrome seems to handle that ? Thanks.

---

### Post by Bucky Ball on 2015-10-03
Just a tip: 14.10 is no longer supported so you won't be installing anything, including flash. 

Advise you upgrade to a supported release, 14.04 LTS, supported until 2019, or 15.04, until January 2016, then install flash with:

```
sudo apt-get install flashplugin-installer
```

Or use Software Centre.

---

### Post by Iflana on 2015-10-04
> **Bucky Ball said:**
> Just a tip: 14.10 is no longer supported so you won't be installing anything, including flash. 

Advise you upgrade to a supported release, 14.04 LTS, supported until 2019, or 15.04, until January 2016, then install flash with:

```
sudo apt-get install flashplugin-installer
```

Or use Software Centre.

I hope the original poster doesn't mind if I chime in here, because I'm also having problems with websites that use Flash in Firefox.  I am using Firefox 41, and have the Adobe Flash plug-in installed via the Ubuntu Software Centre on 14.04.  Some sites work fine, while others claim that there's an outdated version of Flash installed.  Even when clicking "Allow" or "Allow and remember" sites aren't working properlly with Flash.  On those that have problems you're directed to the Adobe site where you can download the version 11 tar.gz file to upgrade.  The instructions are useless telling you to put things in the "appropriate directory" though.  I have no idea where that is!  Also, I'm wondering if this is the same version that's already installed via the Software Centre (or command line as shown above)?

---

### Post by grahammechanical on 2015-10-04
@lflana

This blog post may interest you. It explains the situation.

[http://www.pcworld.com/article/2948115/browsers/mozilla-firefox-temporarily-blocks-flash-by-default.html](http://www.pcworld.com/article/2948115/browsers/mozilla-firefox-temporarily-blocks-flash-by-default.html)

Regards.

---

### Post by jim_deadlock on 2015-10-04
> **Iflana said:**
> Some sites work fine, while others claim that there's an outdated version of Flash installed.

The final version of Adobe Flash for Linux is 11.2, there will be no  further development for Linux. The current version for Windows is 18 or  something, and some websites simply refuse to allow older versions.  There are complicated workarounds, but if you have dual boot or a Win VM  it's easier to just give in and use that for those few tricky websites.

---

### Post by eightbits2010 on 2015-10-04
Bucky Ball: That makes sense and probably explains why the Xubuntu 14.04 version has Firefox 41 installed(?). I am a bit confused that 14.04 LTS should be the system level OS.
Somewhere i was thinking that the 14.10 was a better version than 14.04 (?).
I am not sure how to 'upgrade' to a version number lower than what is installed at this time. I certainly do not want to do a new install if that is what upgrade means.  I need help on understanding
how to go from .10 to .04 ?
I am really not having problems except with using Firefox and accessing Facebook videos. I did notice Chrome seems to work as expected.

---

### Post by eightbits2010 on 2015-10-04
Those are the same experiences I am having, with the exception that using Chrome. So, I am thinking that the issue(s), and there must be more than one issue, is with Firefox and Facebook videos
and as mentioned by the moderator, the actual Ubuntu version.

---

### Post by eightbits2010 on 2015-10-04
Interesting link, thank you for posting the URL. I will continue to keep digging into this. In the meantime i can switch to Chrome if something important on Facebook video(s).
I do prefer to use Firefox over Chrome.

---

### Post by Bucky Ball on 2015-10-04
> **eightbits2010 said:**
> Bucky Ball: That makes sense and probably explains why the Xubuntu 14.04 version has Firefox 41 installed(?). I am a bit confused that 14.04 LTS should be the system level OS.

14.04 LTS is a long-term support release, supported for five years. LTS are released every two years. The next is 16.04 LTS. 14.10 is an 'interim' release. They are supported for nine months.
> Somewhere i was thinking that the 14.10 was a better version than 14.04 (?).

Newer rather than better I'd say. Having to upgrade every six months is not better for me, but that's just me. :)

> I am not sure how to 'upgrade' to a version number lower than what is installed at this time. I certainly do not want to do a new install if that is what upgrade means. 

To revert to 14.04 LTS is a clean install. There is no 'going back' to an older release any other way. I believe you can upgrade from a dead release to a supported one, but you need to change the repositories to do so. I am not au fait with this, but it is the only way you are going up or down without a clean install.

With Pepperflash installed Chromium uses the latest flash. As already mentioned, the last version of flash available for Linux, and still being used and getting security updates, was 11.2.

Hope that helps.

---

### Post by monkeybrain20122 on 2015-10-04
> **jim_deadlock said:**
>   There are complicated workarounds, but if you have dual boot or a Win VM  it's easier to just give in and use that for those few tricky websites.

It is not that complicated to install Chrome for those tricky websites.

---

### Post by 2CV67 on 2015-10-05
I am using 15.04 with FF40.0.3.
Most of the sites I use with Firefox throw up the "Firefox has prevented the outdated plugin "Adobe Flash" from running" warning.
This becomes unbearable.
What are my options?
Is the problem going to go away, or is that the end for the Ubuntu/FF combination?
I do have Chromium which I use for some specific duties, but don't really want to use it in preference to FF all the time... (for philosophical reasons concerning Google & free software).

Thanks!

---

### Post by SeijiSensei on 2015-10-05
I've taken to using the Windows version of FlashPlayer in Linux Firefox by installing [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") then [installing FlashPlayer](http://pipelight.net/cms/plugin-flash.html).

---

