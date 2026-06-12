---
title: "Endless &quot;Web Authentication for Google&quot; prompts"
date: 2017-03-23
forum: General Help
---

### Post by rahidz on 2017-03-23
I'm on Ubuntu 16.10 as of around two weeks ago, today I woke up and was greeted by a prompt asking for a Google Login. I input my username and password assuming this was some system-related process, and the screen proceeded to a page saying 

"GNOME Evolution would like to..." followed by a host of things (reading my email?! is this normal/safe?) it would like to do.

No matter if I click Allow or Deny, or close out of the window, the screen immediately pops back up again. How rude :P

So, what exactly is this dialog, and how do I tell it to bugger off?

Cheers!

Rahid Z.

---

### Post by howefield on 2017-03-23
Could you screenshot it and post it here ?

It would be normal for your google account to authorise applications that want to make use of or otherwise control your google account, for example the ones that do it for me are rclone, rainbowstream and gcalcli. I'm not sure if this is what's happening here but a screenshot may be useful.

---

### Post by rahidz on 2017-03-23
[IMG]http://i.imgur.com/sdKn9RC.png[/IMG]

Sorry for the large image.

And thanks for the info.

---

### Post by howefield on 2017-03-23
Yes, that is a benign message asking for you to authorise your google account to allow interaction with the application. Inputting your google account username and password and clicking allow should be the end of it. If it isn't perhaps you need to go into your google account account settings and allow Evolution as an insecure application. I'll load up evolution and see if I can replicate your issue.

---

### Post by howefield on 2017-03-23
Just to confirm that Evolution appears to be considered as a "less secure" application as far as accessing your gmail account.

To stop the pop-up appearing every time you launch Evolution, you would need to turn on access for this types of application via your google account settings.

[https://myaccount.google.com/security](https://myaccount.google.com/security)

---

### Post by vasa1 on 2017-03-23
> **rahidz said:**
> ...
Sorry for the large image.
...
Next time you take a screenshot, you maybe able to choose the area you want to grab. Alternatively, you could edit the image afterwards. 

And then you could use the paperclip icon found above the area in which you compose your post. That will show you how to upload your image here directly without having to resort to a third-party image-hosting site.

---

### Post by rahidz on 2017-03-23
> **howefield said:**
> Just to confirm that Evolution appears to be considered as a "less secure" application as far as accessing your gmail account.


To stop the pop-up appearing every time you launch Evolution, you would need to turn on access for this types of application via your google account settings.


[https://myaccount.google.com/security](https://myaccount.google.com/security)


Thanks! I went to the Less Secure Apps page, but it did not let me give access to Evolution, instead giving me an error:


> This setting is not available for accounts with 2-Step Verification enabled. Such accounts require an application-specific password for less secure apps access. Learn more


I went to the "Apps connected to your account" page, and revoked Evolution's permissions entirely, I don't trust it and have no need for it since I only check e-mail in Chrome anyway. 

Restarted Ubuntu, however the "Web Authentication for Google" prompt is still there, asking me for an e-mail, and instantly restarting whenever I click the X.

---

### Post by howefield on 2017-03-23
> **rahidz said:**
> Thanks! I went to the Less Secure Apps page, but it did not let me give access to Evolution, instead giving me an error:

Ah, sorry about that, I only tested with a "standard" authentication account but it seems that there is a process for allowing it anyway, as per the error.

> I went to the "Apps connected to your account" page, and revoked Evolution's permissions entirely, I don't trust it and have no need for it since I only check e-mail in Chrome anyway. 

Restarted Ubuntu, however the "Web Authentication for Google" prompt is still there, asking me for an e-mail, and instantly restarting whenever I click the X.

Try purging Evolution from the command line..

```
sudo apt purge evolution
```

Just be careful and watch for packages that it may want to remove.. if your not sure, just post back with the terminal output.

---

### Post by rahidz on 2017-03-23
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'evolution' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


The prompt message popped back up today, this time I was able to log-in and it worked and disappeared. Weird.

Edit: Just restarted, no prompt. Yay?

---

