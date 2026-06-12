---
title: "Using latest flash player on firefox in Ubuntu 13.04"
date: 2013-10-28
forum: General Help
---

### Post by uzumakifahim on 2013-10-28
Hi everybody,
I'm using Firefox 24 on Ubuntu 13.04. I'm watch any online video, flash games without no problems, but recently for just from two days ago a specific website is asking me to update my flash player and I can't get specific feature without updating flash. Point to be noted, using chromimum that site works perfectly, but I love Firefox and want to continue to use that.

Please help me on this regard.

Thanks in advance.

---

### Post by Impavidus on 2013-10-28
You can't. The latest flash is not available on Linux and will never be. Chromium has the latest flash build-in, but this won't happen for firefox.

---

### Post by SeijiSensei on 2013-10-28
You can most certainly have Flash, but no versions past 11.2 will be released.

I activate the "partners" repository, then use "sudo apt-get install adobe-flashplugin".  Works like a charm.

Now if this "specific web site" happens to be Amazon Instant Video, that's a deeper problem.  Amazon and other commercial sites rely on DRM restrictions to control access to content.  On Linux systems that has meant installing the [now-deprecated HAL]("https://wiki.ubuntu.com/Halsectomy").  [Starting with 13.10, the required hal and libhal1 packages are no longer in the repositories]("https://answers.launchpad.net/ubuntu/+source/hal/+question/237614").  I've tried a couple of alternatives like using the Raring releases or the Debian packages mentioned in the link.  So far it hasn't worked for me, so I'm using my PS3 to watch Instant Video now rather than my computer.

If you are still on 13.04, try running "sudo apt-get install hal libhal1" and see if you can watch what you're missing.

---

### Post by uzumakifahim on 2013-11-02
Thanks to everyone for your help. I'm also sorry for late reply. I'll try *sudo apt-get install adobe-flashplugin* and post the result here ASAP.

---

### Post by vasa1 on 2013-11-02
> **uzumakifahim said:**
> Hi everybody,
I'm using Firefox 24 on Ubuntu 13.04. I'm watch any online video, flash games without no problems, but recently for just from two days ago a specific website is asking me to update my flash player and I can't get specific feature without updating flash. Point to be noted, using chromimum that site works perfectly, but I love Firefox and want to continue to use that.

Please help me on this regard.

Thanks in advance.
Why don't you provide the link to this specific website?

---

### Post by vasa1 on 2013-11-02
> **Impavidus said:**
> You can't. The latest flash is not available on Linux and will never be. **Chromium has the latest flash build-in**, but this won't happen for firefox.
Chrome does. I don't think Chromium does by default.

---

### Post by uzumakifahim on 2013-11-02
That site is elance.com, a freelancing site. I can upload any file on this site, it's saying I need to upgrade my flash player. :(

There is one more thing, no luck with *sudo apt-get install adobe-flashplugin.*

---

### Post by SeijiSensei on 2013-11-02
Did you activate the partners repository like I said?  Either do it through your GUI package manager, or remove the leading hash mark ("#") from the line:
```
deb http://archive.canonical.com/ubuntu raring partner
```
in /etc/apt/sources.list ("sudo nano /etc/apt/sources.list").

Then run "sudo apt-get update" to refresh the repository manifests, followed by "sudo apt-get install adobe-flashplugin".  I'm running Kubuntu 13.04 on this machine with Flash installed that way.

---

### Post by warp99 on 2013-11-02
Did you enable the partner repos in the Software & Updates application under "Other Sources"?

[http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository](http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository)

Of course change "maverick" to "raring" for 13.04.

---

### Post by yoramdavid on 2013-11-02
Hi all,

I am having a similar problem. Some videos on this same site will play, others do not. Since it is the same problem and might help, I am using this post instead of opening a new one.
I already followed what was mentioned here, flash-plugin is installed correctly.

This is a video that **[does not play]("http://www.gandacena.net/videos/joao-baiao-cria-versao-portuguesa-da-musica-gangnam-style")**.
This is a video that **[does play]("http://www.gandacena.net/videos/um-kit-de-unhas-fantastico-vale-pena-assistir")**.

I tested on chromium web browser and it also does not work.

Regards and thanks.

David.

---

### Post by warp99 on 2013-11-02
> **yoramdavid said:**
> 
I tested on chromium web browser and it also does not work.


That's because Chromium and Firefox use the Adobe flash plugin, which is deprecated. If you install Chrome direct from Google with the "Pepper" flash plugin both videos will play without a problem:

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

This will also add the Google repository to your sources.list so updates will be available through the Ubuntu Software Updater. Just remember to remove all of the Chromium packages from your system before installing Chrome:

```
sudo apt-get remove chromium*
```

---

### Post by vasa1 on 2013-11-02
> **warp99 said:**
> That's because Chromium and Firefox use the Adobe flash plugin, which is deprecated. If you install Chrome direct from Google with the "Pepper" flash plugin both videos will play without a problem:

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

This will also add the Google repository to your sources.list so updates will be available through the Ubuntu Software Updater. Just remember to remove all of the Chromium packages from your system before installing Chrome:

```
sudo apt-get remove chromium*
```
IMO, removing Chromium isn't necessary if one wants to install Chrome. They have separate profile folders. Of course, having both maybe a bit unnecessary!

---

### Post by warp99 on 2013-11-02
> **vasa1 said:**
> Of course, having both maybe a bit unnecessary!

;-)

---

### Post by uzumakifahim on 2013-11-02
Sorry, maybe I need to be more specific. I've said "[COLOR=#000000]no luck with [/COLOR]*sudo apt-get install adobe-flashplugin* ", to mean that, I use that specific site properly even after successful installation of adobe-flashplugin. I've no problem with installing adobe-flashplugin, but only with firefox with a specific site.

---

### Post by Impavidus on 2013-11-02
Then, as indicated in post #2, your flash is too old and there is no newer flash for Firefox on Linux available. It's time for those websites to move over to html5 with open codecs. In the meantime, avoid those sites or use Chrome or Chromium.

---

### Post by yoramdavid on 2013-11-02
> **warp99 said:**
> That's because Chromium and Firefox use the Adobe flash plugin, which is deprecated. If you install Chrome direct from Google with the "Pepper" flash plugin both videos will play without a problem:

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

This will also add the Google repository to your sources.list so updates will be available through the Ubuntu Software Updater. Just remember to remove all of the Chromium packages from your system before installing Chrome:

```
sudo apt-get remove chromium*
```

Indeed it works with Chrome. I thought Chrome and Chromium were the same family / origin.
A pity we cannot use the pepper plugin in firefox.

Thanks.

---

### Post by Frogs Hair on 2013-11-02
Disregard

---

### Post by uzumakifahim on 2013-11-02
Okay, if that's the case, then I'm gonna mark this thread as solved.

Thanks to all for your help.

---

