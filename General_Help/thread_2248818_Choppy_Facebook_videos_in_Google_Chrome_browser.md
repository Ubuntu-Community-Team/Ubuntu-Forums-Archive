---
title: "Choppy Facebook videos in Google Chrome browser"
date: 2014-10-17
forum: General Help
---

### Post by michael-piziak on 2014-10-17
I experience very choppy videos when I click a video on facebook.  Anyone else experience this or have a cure ?

p.s. videos work fine in Firefox browser

---

### Post by slickymaster on 2014-10-17
Can not speak about videos on facebook since I don't have an account, but I'm not facing any issues watching videos in general with the latest Chrome```
~$ apt-cache policy google-chrome-stable:
google-chrome-stable
  Installed: 38.0.2125.104-1
  Candidate: 38.0.2125.104-1
  Version table:
 *** 38.0.2125.104-1 0
        500 http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by michael-piziak on 2014-10-17
Youtube videos work fine, but the ones in facebook are choppy.  I didn't have an issue until upgrading from 12.04 to 14.x lts

Perhaps someone can give me the code to uninstall and then the code to reinstall Chrome and see if that helps.

---

### Post by slickymaster on 2014-10-17
How did you install it? Did you add the Google Chrome PPA to your repositories or did you download the .deb file?

---

### Post by michael-piziak on 2014-10-17
> **slickymaster said:**
> How did you install it? Did you add the Google Chrome PPA to your repositories or did you download the .deb file?

I installed from a Google Chrome link, so probably the .deb file.

Here is a snapshot of my "chrome:plugins" screen

I was probably using a previous version of Chrom when I had 12.04 lts.  Perhaps uninstalling this version and someone installing a previous version would work - ?

---

### Post by slickymaster on 2014-10-17
> **michael-piziak said:**
> I installed from a Google Chrome link, so probably the .deb file.

Here is a snapshot of my "chrome:plugins" screen

I was probably using a previous version of Chrom when I had 12.04 lts.  Perhaps uninstalling this version and someone installing a previous version would work - ?

Can you please post back the output you get from```
apt-cache policy google-chrome-stable
```

---

### Post by michael-piziak on 2014-10-17
> **slickymaster said:**
> Can you please post back the output you get from```
apt-cache policy google-chrome-stable
```

I get this:

google-chrome-stable:
  Installed: 38.0.2125.104-1
  Candidate: 38.0.2125.104-1
  Version table:
 *** 38.0.2125.104-1 0
        500 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages
        100 /var/lib/dpkg/status
N: Ignoring file 'google.listtaffy' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google.listtaffy' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 



Thanks for continuing to try to help me.  Note:  Video is only choppy viewing facebook videos using Chrome or Chromium (I tested both browsers).  Youtube works fine on both browsers.

---

### Post by slickymaster on 2014-10-17
> **michael-piziak said:**
> I get this:

google-chrome-stable:
  Installed: 38.0.2125.104-1
  Candidate: 38.0.2125.104-1
  Version table:
 *** 38.0.2125.104-1 0
        500 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages
        100 /var/lib/dpkg/status
N: Ignoring file 'google.listtaffy' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google.listtaffy' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ 

Thanks for continuing to try to help me.  Note:  Video is only choppy viewing facebook videos using Chrome or Chromium (I tested both browsers).  Youtube works fine on both browsers.


Not sure if you'd solve your problem just by installing a previous version of Chrome and also you're getting a warning which might, or not, be somehow related.

Let's first try to fix that. In a terminal run the following:```
sudo mv /etc/apt/sources.list.d/google.listtaffy /etc/apt/sources.list.d/google.list
```I thinks this should work as the file currently has the name google.listaffy, but it needs to end in *.list to work.

---

### Post by michael-piziak on 2014-10-17
> **slickymaster said:**
> Not sure if you'd solve your problem just by installing a previous version of Chrome and also you're getting a warning which might, or not, be somehow related.

Let's first try to fix that. In a terminal run the following:```
sudo mv /etc/apt/sources.list.d/google.listtaffy /etc/apt/sources.list.d/google.list
```I thinks this should work as the file currently has the name google.listaffy, but it needs to end in *.list to work.


ok I ran that code in terminal, restarted, and still choppy video in facebook

---

### Post by slickymaster on 2014-10-17
> **michael-piziak said:**
> ok I ran that code in terminal, restarted, and still choppy video in facebook

Well that wasn't supposed to fix the video choppiness. ;) Just to fix your **sources.list** file.

As to you original issue I must say that I'm not seeing anything that might help you, as it might well be related to something within the facebook site itself, since you say that's the only one showing that problem.

Maybe someone else will step in the thread with other ideas/solutions.

---

### Post by michael-piziak on 2014-10-17
ok thanks for your assistance and yes I hope someone can step in with other ideas/solutions

Interesting, using Firefox browser all works fine.  But I always use to use Chrome before (as before Firefox gave me some problems).  I like to have a couple browsers anyways so if a site isn't working on one browser then I use the other.

sidenote:  I tried to install pepper flash for chrome, but couldn't figure out which command to install it for the chrome stable version.  Also, I don't think it's the facebook page, because all worked fine yesterday before I went from 12.04 lts to 14.x lts

Update:  I viewed system monitor and when using Chrome cpu1 and cpu2 take turns maxing out at 100%.  In Firefox, cpu1 an cpu2 stay around 50%

---

