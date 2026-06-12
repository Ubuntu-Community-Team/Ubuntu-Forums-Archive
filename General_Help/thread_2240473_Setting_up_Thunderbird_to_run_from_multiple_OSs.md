---
title: "Setting up Thunderbird to run from multiple OSs"
date: 2014-08-20
forum: General Help
---

### Post by veddox on 2014-08-20
I'm triple-booting my laptop with Windows 7, Ubuntu 14.04 and Arch Linux. I would like to set up Thunderbird so that it uses the same folder for all operating systems, but have not yet managed to do so. I have a shared data partition that everyone has access to, so I copied the .thunderbird folder from my Ubuntu home folder there. (I had originally set Thunderbird up with Ubuntu.) I managed to set the preferences in such a way that any incoming mail is stored in this new folder. However, there are still some problems:

First of all, my message filters don't run anymore. They give me an error message saying they could not find the subfolders of my inbox into which they were supposed to move select mails, although I can move them manually no problem. Secondly, I have Lightning calendar installed as an add-on. It works great under Ubuntu, but the Arch version can't find any of my entries, and I haven't yet figured out how to tell it what directory it should use. Finally, whenever I use Arch it somehow loses track of what messages I have already downloaded, and keeps downloading the same messages over and over again.

I realize this might sound a bit confusing, but I hope somebody here has some experience with a similar setup. Thanks a lot in advance for any help!

---

### Post by oldfred on 2014-08-20
When you say you set preferences, did you change profile.ini?

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I do not have calendar and only have used XP, and many versions of Ubuntu since 6.06 with my same shared profiles for Thunderbird and Firefox without issue. It did not like some of the Windows add-ons in Linux, but now that I am not running XP, I do not get those messages either. But it has just worked.

---

### Post by nerdtron on 2014-08-20
My way of doing this when I use thunderbird on multiple computers is setup filters and folders on the email server itself. We have a webmail that we access on the browser and there I set up the filters and folders.

Now when I open thunderbird on any computer using IMAP connection all my folder are there.

---

### Post by oldfred on 2014-08-20
Do not know about that type of configuration.

---

### Post by veddox on 2014-08-20
@nerdtron: thanks for the suggestion, but I only check my mails on one computer. Also, I will soon be moving to an environment where every kilobyte of downloads is precious, so I think I prefer to get them onto my computer with pop3

@oldfred: thanks for the links! I set the preferences using the graphic in-program menu, but I'll have a look at what you sent me there.

---

### Post by amanchesterman on 2014-08-21
As a supplement, there's a Mozilla article specifically about [using a shared folder](https://support.mozilla.org/en-US/kb/exporting-and-sharing-a-calendar) to enable several instances of Thunderbird to access a single calendar, which I think is close to what you want to achieve? Hope this helps.

---

### Post by Irihapeti on 2014-08-21
I recall trying to do this a few years ago. I got stuck with the message filters because the paths of the message folders are different on Windows and Linux systems. You might be able to do something with symlinks, though I have my doubts.

---

