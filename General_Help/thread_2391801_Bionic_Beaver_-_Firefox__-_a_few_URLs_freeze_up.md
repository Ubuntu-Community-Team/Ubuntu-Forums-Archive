---
title: "Bionic Beaver - Firefox  - a few URLs freeze up"
date: 2018-05-13
forum: General Help
---

### Post by dpg1 on 2018-05-13
Since I created an account here to make my previous post, I'll add this other issue I've run into that I appeared after upgrading to 18.04.

I have seen firefox hang on a few websites which did not have any problems on previous versions of Ubuntu/firefox and don't have trouble with Chrome on 18.04.

The simplest url I have found to see is this is

    [https://txhighway.com/](https://txhighway.com/)

This worked fine for me on ubuntu 16.04, and it works fine on Chrome on 18.04.   But the default firefox install on 18.04 just hangs for me after a few seconds.  I've seen this on two different fresh installs of Bionic Beaver.

The other web site which I had trouble with it completely locking up was FAAsafety.gov

Actually I'm not sure locking up is the correct term.  I feel like it might just be deadlocked or such, as sometimes it feels like it might be making small progress after coming to a stop.

Not affiliated with either web site.

--

Firefox version: 60.0 (64-bit) Mozilla Firefox for Ubuntu canonical - 1.0
Linux kairos 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
model name      : Intel(R) Core(TM) i5-3330 CPU @ 3.00GHz

---

### Post by missmoondog on 2018-05-14
absolutely no help here, but fwiw, both those links open up for me very quickly in firefox.

usually when a site doesn't work when it used to, it comes down to some addon or extension.

---

### Post by SeijiSensei on 2018-05-14
Go to Tools > Add-ons and check to see if any extensions or plugins are disabled.  Firefox made a major change to how its extensions work, and some have never been updated to the new methods.  Firefox will tell you whether it has disabled any add-ons.

On my Kubuntu 18.04 i5 machine with Firefox 60 and kernel 4.15-20, those sites load correctly.

You could try running in "safe mode" from the command prompt with:
```
firefox --safe-mode &
```
which disables all extensions and themes.  If that works, then it's likely the problem lies in a dodgy extension.

---

### Post by walts48 on 2018-05-14
Both sites load fast for me using the Ubuntu build of Firefox on 16.04 LTS.

Try the Standard Troubleshooting Procedures of Help > Restart with Add-ons Disabled. If that doesn't help, try a test profile.

Type about:profiles into the address bar, click the Create a New Profile button, give it a name, click Finish, find the profile, click the Launch profile in new browser button.

A new window will open using that profile. Test the sites in that profile.

If the sites work in safe mode you need to track down which extension(s) caused the problem.

---

### Post by dpg1 on 2018-08-07
This happened to me on two different systems in two different environments, both as a fresh build.
So I uninstalled firefox and installed the snap version and that seemed to resolve the problem.  After a time, I eventually got frustrated with the snap version and went back to the apt version and the problem simply resolved itself.

What I wanted to do was recreate the problem by booting from the install media, but I ran out of time to troubleshoot it any further.  When the problem appeared, I simply switched to Chrome. 

In my opinion, there was a problem.  I had also passed the information on to Firefox, so perhaps they found and resolved it in the mean time.

Anyway,  thanks much for your kind assistance.

---

### Post by unseeni on 2019-01-14
I just upgraded from lubuntu 16.04 LTS to 18.04 LTS. After the upgrade the whole operating system started to freeze randomly. It seems to be happening only when Firefox (64.0, 64bit canonical-1.0) is running. There was no such problem on 16.04.  Edit: At first I thought it was the firefox addons, and disabling them did seem to make the freezes less frequent. Then I stumbled upon this [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) bug. It seemed like it would explain everything, but the C6 disabling did not seem to stop the freezing.. so I just booted with older kernel, and the system seems to be quite stable (so far) even with all addons on.

---

### Post by Boorhin on 2019-01-31
> **unseeni said:**
> I just upgraded from lubuntu 16.04 LTS to 18.04 LTS. After the upgrade the whole operating system started to freeze randomly. It seems to be happening only when Firefox (64.0, 64bit canonical-1.0) is running. There was no such problem on 16.04.  Edit: At first I thought it was the firefox addons, and disabling them did seem to make the freezes less frequent. Then I stumbled upon this [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) bug. It seemed like it would explain everything, but the C6 disabling did not seem to stop the freezing.. so I just booted with older kernel, and the system seems to be quite stable (so far) even with all addons on.

Could you precise which Kernel? I am having this issue since a month and it is driving me crazy. I am on the edge of getting rid of Firefox all together. There is no documentation anywhere or report that seems to fit this issue. Although it is almost impossible to work. I don't think it is url-related some have suggested a memory leak but I have not noticed any. Gnome basically freezes and I need to hard reset.

Thanks

---

### Post by unseeni on 2019-02-11
4.4.0-141-generic is the kernel that seems to be working for me.

4.15.0-44-generic and 4.15.0-45-generic kernels kept freezing my system randomly when firefox was running. It did not seem to be related to any URL, addon or memory leak in my case.. I have no idea what it was, but booting this older kernel fixed it for me.

---

