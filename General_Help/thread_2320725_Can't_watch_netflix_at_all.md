---
title: "Can't watch netflix at all?"
date: 2016-04-16
forum: General Help
---

### Post by autonenterprises on 2016-04-16
I just installed Ubuntu again, linux again for the first time in about 3 or 4 years. Nice to be back, except: I tried to watch Netflix with every browser I can download and nothing worked. There is apparently a security library or discrepancy that prevents any Linux browser from running Netflix at this time. I searched the web and apparently there's no way to watch Netflix on Linux at all right now? If I'm wrong please let me know because that really sucks.

---

### Post by yancek on 2016-04-16
You should be able to watch Netflix using pipelight which is explained in detail at the link below.  Google-chrome should also work by default.

 [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by Le3eVolfoni on 2016-04-16
You can watch Netflix natively with google chrome browser (thanks to html5). The bad news is that you can have an up to date version of chrome on your ubuntu only if it is a 64-bits version.

---

### Post by autonenterprises on 2016-04-16
Thank you for your responses. It was my understanding that Chrome is no longer supported or available for Linux. One has to use chromium which I know does not work with Netflix. Am I wrong on either of those issues?

---

### Post by oldos2er on 2016-04-16
Chrome is most certainly available for Linux: [https://www.google.com/chrome/browser/desktop/](https://www.google.com/chrome/browser/desktop/)

---

### Post by yancek on 2016-04-16
My understanding is that chrome has dropped support for 32bit Linux.

[http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

---

### Post by DanglingPointer on 2016-04-17
If you're on 64bit linux, then just download Chrome. It works! I've got it at home!

---

### Post by Habitual on 2016-04-18
Or continue to use 32 bit Google Chrome, but with no updates...

---

### Post by mörgæs on 2016-04-18
Using a browser without security updates is not what we normally recommend.

---

### Post by efflandt on 2016-04-18
I have never gotten pipelight with MS Silverlight to work in firefox for anything that requires Silverlight. But Google Chrome (which as mentioned is now 64-bit only) works fine for Netflix using HTML5.

However, Linux Google Chrome does not have whatever is needed in its pepperflash for protected content that Hulu implemented some time last year I think (about the time they got ShowTime). So for Hulu you need to use firefox/flash, and have to find the ppa to install hal from an earlier Ubuntu version. Example: [http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up](http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up)

---

### Post by SeijiSensei on 2016-04-19
> **efflandt said:**
> I have never gotten pipelight with MS Silverlight to work in firefox for anything that requires Silverlight. But Google Chrome (which as mentioned is now 64-bit only) works fine for Netflix using HTML5.
I routinely watch Netflix with pipelight.  Perhaps you did not specify the correct User-Agent string?

I use the [**UAControl**]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") extension for Firefox and this User-Agent string
```
Mozilla/5.0 (Windows NT 10.0; rv:41.0) Gecko/20100101 Firefox/41.0
```
At some point Netflix might stop working because the UA string refers to a version of Firefox that is too far out-of-date.  In that case, you can probably just update the version number, 41.0 in this case, to match the version of Firefox for Linux shown in Help > About.  If that doesn't work, upgrade Firefox on a Windows machine to the latest version and grab the UA string from that.  The one I posted is up-to-date and should work for quite some time.

---

### Post by oldos2er on 2016-04-19
> **efflandt said:**
> I have never gotten pipelight with MS Silverlight to work in firefox for anything that requires Silverlight. But Google Chrome (which as mentioned is now 64-bit only) works fine for Netflix using HTML5.

However, Linux Google Chrome does not have whatever is needed in its pepperflash for protected content that Hulu implemented some time last year I think 

I haven't had any problem watching Hulu with Google Chrome (v50.0.2661.75).

---

### Post by deadflowr on 2016-04-19
> **oldos2er said:**
> I haven't had any problem watching Hulu with Google Chrome (v50.0.2661.75).

Interesting.
It seems like hulu now will use an html5 player on chrome (right click shows Hulu Player 5.XXX-something-or-other)

---

