---
title: "Adobe Flash Player"
date: 2013-06-03
forum: General Help
---

### Post by Silvertones on 2013-06-03
What's thee trick to getting Flash working on 10.04.
Thanks.

---

### Post by fantab on 2013-06-03
10.04 is DEAD. No more security and other updates. Upgrade you Ubuntu version to 12.04 or later.

---

### Post by Silvertones on 2013-06-04
> **fantab said:**
> 10.04 is DEAD. No more security and other updates. Upgrade you Ubuntu version to 12.04 or later.
This doesn't answer my question. My computer will not run anything above 10.04.
How about an answer to my question?

---

### Post by Charlotte18 on 2013-06-04
> **Silvertones said:**
> What's thee trick to getting Flash working on 10.04.
Thanks.
Go to adobe's archive site for flash player and download the zip archive for flash 10.3. Unzip the archive. Open the folder. Unzip the tar.gz "linux" archive. Open the folder. Finally, copy and paste the libflashplayer.so file into the appropriate folder where your web browser will see it (/usr/lib/chromium-browser/plugins, /usr/lib/firefox/browser/plugins, or whatever it is for your browser).

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

---

### Post by philinux on 2013-06-04
> **Silvertones said:**
> This doesn't answer my question. My computer will not run anything above 10.04.
How about an answer to my question?

you need an archive version from adobe. Version 10 works IIRC.

---

### Post by 3rdalbum on 2013-06-04
> **Silvertones said:**
> This doesn't answer my question. My computer will not run anything above 10.04.
How about an answer to my question?

Running an unsupported operating system is a really, really bad idea:

a. Security issues
b. No new hardware support (what happens when your printer dies? You won't just be able to use a new one)
c. Support on the forums will dry up as people forget what 10.04 was like, and forget its quirks and no longer be able to give you any useful help. Heck, I think we've already passed that point.

Just because there are no supported versions of Ubuntu that work on your computer, does not mean you are stuck with Ubuntu 10.04. There is Xubuntu 12.04 and Lubuntu 12.04 which support non-PAE CPUs. Have you tried those? There are also modern Linux distros that have been built from the ground up for older computers.

---

### Post by Charlotte18 on 2013-06-04
Why argue with what someone wants to do?

Just follow my instructions above. I believe flash will be working then.

---

### Post by BBQdave on 2013-06-04
> **3rdalbum said:**
> Running an unsupported operating system is a really, really bad idea...

Running Xubuntu 12.04 might gain you more time with old hardware, and your system would be up to date :)

---

### Post by 3rdalbum on 2013-06-04
> **Charlotte18 said:**
> Why argue with what someone wants to do?

Just follow my instructions above. I believe flash will be working then.

I believe in fixing the root problem instead of the symptom.

---

### Post by fantab on 2013-06-05
> **3rdalbum said:**
> I believe in fixing the root problem instead of the symptom.

+1.

If OP has problem installing Ubuntu 12.04 then he should start a new thread specifying the problem. Also, as suggested, Xubuntu and Lubuntu offer great alternatives, as both need far less system resources than Ubuntu.

---

### Post by Charlotte18 on 2013-06-05
You're assuming ignorance on the OP's part, as if the OP hasn't realized that 10.04 is out of date. The OP wants to run flash in 10.04. I believe this can be done fairly easily.

Did the OP ask for a lecture on his chosen setup? Many questions here seem to be answered with some version of the admonitory response: *I could tell you how to do what you want to do, but I won't tell you how, because I disagree that you should want to do what you want to do.* I don't mind advising someone to upgrade, but why not say, *Here's how you run flash on 10.04, but if I were you, I'd switch to lubuntu*?

---

### Post by fantab on 2013-06-05
The simplest and safest way of installing flash in Ubuntu is via Ubuntu Repositories. The software in Repos is 'Tested' to run with ubuntu. OP cannot do that. Why? Because the version he is using has reached its 'end of life'. If OP installs flash directly there could be other dependency issues because dependencies won't be upgraded. So OP has to upgrade to newer version of Ubuntu or if he has problems running heavier on resources UNITY then he/she can opt for lighter desktops like Xubuntu or Lubuntu or if she/he loves older gnome then 'gnome classic'.

The real problem is an outdated version of Ubuntu causing the 'headache' to the OP. Its not Flash.

---

### Post by Charlotte18 on 2013-06-05
> So OP has to upgrade to newer version of Ubuntu That's a subjective question for you philosophers here. For all we know, the OP might enjoy trying to keep an old OS going for as long as possible. Who am I to judge?

If the OP just wants flash to work in 10.04, all he has to do is follow my advice in the fourth post of this thread.

---

