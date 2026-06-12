---
title: "Firefox and Thunderbird crashing as well as graphics issues"
date: 2015-10-19
forum: General Help
---

### Post by Zeikcied on 2015-10-19
My mom has a Dell computer.  Specifically this model from Best Buy: [http://www.bestbuy.com/site/dell-inspiron-desktop-intel-pentium-4gb-memory-500gb-hard-drive-black/2153018.p?id=1219530046281](http://www.bestbuy.com/site/dell-inspiron-desktop-intel-pentium-4gb-memory-500gb-hard-drive-black/2153018.p?id=1219530046281)

She has Kubuntu 14.04 LTS installed on it.  Now, Firefox has a tendency to freeze on occasion when browsing MSN.com, as well as a local news station's website.  Thunderbird has also frozen on one or two occasions, though I don't know why that is.  Any idea why this may be?

Also, the computer turns off the monitor after so much activity, which is normal and expected.  But when it wakes up, occasionally there are some graphical glitches on Thunderbird (which she keeps open all the time) such as the window being completely yellow or white or even black.  I think I read about a bug in the Intel graphics driver a few months ago that seems related to this, but it said it was fixed.  Don't know if it was ported back to 14.04 or not, though.

With the new *Ubuntu versions coming out in a few days, I was even wondering if I should keep her on Kubuntu or move her to a lightweight desktop like Xubuntu or Lubuntu.  I think she may prefer to stay on Kubuntu, but I don't know if that may be part of the problem.  Like, could these crashes be caused by the computer not being powerful enough for KDE?  Or is it purely a Firefox/Thunderbird issue?

She likes using Firefox mainly because of the old 1Click Weather add-on from Weather.com.  Someone adapted the add-on to work past its expiration date, so to speak, and there really hasn't been any other add-on that uses Weather.com.  At least not one that's been regularly updated.  I don't know if I could get her to use Chrome or not.

---

### Post by SeijiSensei on 2015-10-20
Are those Flash-heavy sites? MSN is almost certainly optimized for Internet Explorer.  Maybe it uses Silverlight?  Try [this](http://pipelight.net/cms/about.html).  I run both Silverlight and the Windows version of FlashPlayer through pipelight.

As for Thunderbird stalling, it could have as much to do with her email provider as Thunderbird itself.  I never have stalling, but I run my own mail servers.  Does she use IMAP?  POP?  Does she have a lot of locally-archived mail? Updating a large folder that hasn't been used for some time can take a while.  Does the stalling happen during receiving, sending, or both?

What kernel is she running?  I did a dist-upgrade to Kubuntu 14.04 the other day and am now on 3.16.0-50-generic.  Maybe that includes the updated Intel driver.  I only have the kernel headers and not the source tree, but the files in /usr/src/linux-headers-3.16.0-50-generic/include/config/drm/i915 are dated October 2.

---

### Post by buzzingrobot on 2015-10-20
That's  not the most powerful of machines, so moving to Xubuntu or Lubuntu might make a difference, but without knowing the specific cause of the problems, I'd be reluctant. Plus, if the problem is caused by an application and you use that same application on Xubuntu or Lubuntu, it's likely to behave the same way.

What you do know is that the problems are seen on those two Mozilla products, Firefox and Thunderbird. Both have settings to enable/disable smooth scrolling and hardware acceleration. I doubt they're the fix, but give them a try.

Disable all extensions and plugins in Firefox and Thunderbird.  Quit and relaunch them, then use the app long enough to see if the problem is still there.  If it is not, then enable the extensions/plugins one at a time and then use the app long enough to notice if the problem returns. With luck, you may find the culprit.

If Firefox and Thunderbird are kept open constantly, it's possible they're slowly gobbling an increasing amount of memory. (Diito for any other app that's open all the time.  Memory leaks shouldn't happen, but they do.)  You can run System Monitor to see what's going on over time (here, Firefox normally grabs around 300 mb at launch, and adds about 100mb with every open tab.) If that seems to be an issue, try closing and reopening both once a day.

While I haven't seen Thunderbird lock up as you describe, I have seen Evolution do that when it wasn't able to reconnect with the server, often after the machine woke from suspend.

I agree that Flash and whatever else is used at msn.com might impact things.  Flash used in Firefox on Linux stills gets security patches from Adobe, but hasn't seen any new features for a few years. Meanwhile, of course, sites targeting Windows are going to use current capabilities. Chrome for Linux comes equipped with a different version of Flash that does stay current.

KDE's visual effects can be turned off.  Look in System Settings->Desktop Effects, if you haven't already.  There is a general tab to turn all effects off, but I find I need to use one of the other tabs to disable effects individually.  You'll also see an "Advanced" tab there to choose between OpenGL or Xrender.  I will guess it's using Xrender by default.  If not, try it. (Be careful about playing with the other settings there;  I've seen the screen go black and stay black after a reboot. Very annoying.)

---

### Post by Zeikcied on 2015-10-20
Yeah, it's not a super-powerful machine, but her last computer was almost a decade old, and was really showing its age.  Also, she only ever does web browsing, email, and LibreOffice stuff.  As well as the occasional loading of photos from a camera or tablet with Digikam.  She doesn't really need a powerful machine, and we were trying to keep costs down, as well.

I updated her kernel last night, and I don't know if that fixed the graphics issues or not.

Her Thunderbird doesn't have any add-ons or extensions that I know of.  Heck, I don't quite understand how to even get add-ons or extensions for Thunderbird, so that won't be an issue.  I don't know if it only froze the one time last night or what, but I think she said it did it before.  She likes keeping it open instead of constantly opening and closing it.  Also, her computer (like mine) is on all the time, so Thunderbird is open for an extremely long time.  As far as I know, though, it hasn't frozen too often.  She hasn't complained about it before, so it could just be a more rare occurrence.

She does have a ton of archived messages.  She has I think over 2,000 in her Sent folder, alone.  I know she should probably clean it out, but I don't know if she will.  I think it froze when checking for messages from the POP server.

Her Firefox only has a couple add-ons, that I put on there.  I added Adblock Plus last night, thinking that maybe removing some ads from MSN might help its performance.  I'm not sure if I should uncheck the box that allows non-intrusive ads or not, though.  I disabled the 1Click Weather add-on.  I remember having problems with that after it was discontinued.  Certain sites would cause Firefox to freeze, and disabling it got rid of the crashes.  Problem is, she really likes it and likes having an easy way to our local weather on Weather.com.  Not to mention the easy access to weather alerts.  I could get her ForecastFox, but that's not Weather.com, which she prefers.  So I don't know what to do if that ends up being the solution to the problem.

---

### Post by SeijiSensei on 2015-10-20
Does she have her POP account configured to leave mail on the server?  That's a very intensive process since Thunderbird has to compare the contents of her local storage to the contents of her mailbox on the server when it retrieves new messages.  If she only retrieves mail using this computer, then turn off that option.  If she wants to retrieve her mail from multiple locations, she should be using IMAP instead of POP.

I don't see much difference among the various weather providers myself.  I use either Accuweather or WeatherBug on my Android phone, and [ForecastFox (fixed)]("https://addons.mozilla.org/en-US/firefox/addon/forecastfox-fix-version/"), which uses Accuweather, on Firefox.  I like WeatherBug because it has a database with all the little local stations like schools, fire stations, libraries, and the like.  One of them was at a school across the street from where my daughter went to college, so I always knew what her local weather was.  My phone points to our local high school a few blocks away. ForecastFox puts those handy little icons and popups in the status bar.  I rarely visit the Accuweather site itself.

Run "top" from the command line and look at the memory in use.  Don't worry if it looks like it is all in use; it should be.  The memory not being used for programs is used to cache disk transactions instead.  Here's what my 8 GB machine looks like:
```

top - 20:57:45 up 2 days,  8:43, 14 users,  load average: 0.09, 0.16, 0.21
Tasks: 229 total,   2 running, 226 sleeping,   0 stopped,   1 zombie
%Cpu(s):  1.3 us,  0.3 sy,  0.0 ni, 98.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8044208 total,  7508804 used,   535404 free,   364928 buffers
KiB Swap: 15998972 total,        0 used, 15998972 free.  5470412 cached Mem

```
This is with Kubuntu 14.04 and an Intel i5.  My load averages are very low; the first figure is instantaneous, the others are medium- and long-term averages.  On desktop machines those numbers should be well under two, especially the long-term average.  If they're not, the machine is pretty hard at work.  As for memory, I have 8.0 G total, but 5.47 G of that is used to cache disk transactions.  The programs themselves are only occupying about 2 G.  I set aside 16 G of disk space for swap; so far Linux hasn't found a need for any of it.

The most effective single upgrade you can buy is more memory. If top shows most of the memory in use and little available for caching, I'd invest in memory.  A little browsing shows a compatible [8 GB stick is about $42]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211871&cm_mmc=CNETFindMEMUS-_-20-211-871-_-na-_-na").  The listing says its "laptop memory," but it's the one the Newegg memory finder returns for an Inspiron 3646.  Just look in the box and compare.

---

### Post by Zeikcied on 2015-10-20
She doesn't have the POP settings to leave the emails on the server.  So that shouldn't be the issue.

She says she hasn't had any problems yet today, but she hasn't been on the computer all that much today, either.  But so far so good.  I'm still wondering if Xubuntu or Lubuntu would be better for her computer, but I guess I can at least wait to see how Kubuntu 15.10 works on her system.  I'm giving her system a fresh install when the new version hits instead of waiting for the next LTS in hopes the graphics issues are all fixed.  Assuming they aren't, already.

---

### Post by SeijiSensei on 2015-10-20
If she's not using 15.04 now, I would definitely not upgrade to 15.10.  The most recent Kubuntu versions have been built on KDE5 which I found buggy when I tested 15.04.  It's also different enough from KDE4 that your mother might not like having to make the switch. Just make sure you've upgraded to the most recent kernel and stick with 14.04 until next April.  If you do want to try and upgrade, at least give her a chance to work with the distribution ISO in "Try Ubuntu" mode so she can take it for a test-drive.

---

### Post by Zeikcied on 2015-10-20
> **SeijiSensei said:**
> If she's not using 15.04 now, I would definitely not upgrade to 15.10.  The most recent Kubuntu versions have been built on KDE5 which I found buggy when I tested 15.04.  It's also different enough from KDE4 that your mother might not like having to make the switch. Just make sure you've upgraded to the most recent kernel and stick with 14.04 until next April.  If you do want to try and upgrade, at least give her a chance to work with the distribution ISO in "Try Ubuntu" mode so she can take it for a test-drive.

Plasma 5 in Kubuntu 15.04 is buggy, yes.  I have that on my computer.  I've read on the Kubuntu Forums that the current version of Plasma 5 that ships with 15.10 is a lot better in that regard, so I'm optimistic.

As for whether or not she'll like it, she's not really against change.  As long as I can get the environment set up the way it was, which I should be able to, I'm sure she'll like it.  She's not too concerned with how it looks, as long as it works.

---

