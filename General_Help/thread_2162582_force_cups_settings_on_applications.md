---
title: "force cups settings on applications"
date: 2013-07-15
forum: General Help
---

### Post by etherape88 on 2013-07-15
Hi, 

 I want to enforce the default printer settings of CUPS clients because some users in my network don't have the patience to check their printer settings. For example I have a profile which has the defaults set as duplex in color with an A4 format. But the user and application can override this. Which sometimes happens. I want these profiles to be absolute and unchangeable. I haven't found a way to do this yet. 
 So to clarify again. I want to have a few profiles with printer defaults which can't be overridden by the user or application. This needs to be configured at the server side, not the client. An open profile will be included as well with the freedom to change the settings. The others are locked. 
 I hope someone can point me in the right direction for this one, I've searched for hours but I haven't found anything useful yet. There also seems to be a lack of community support for this since I can't find any official and sizable CUPS community. 
 
 Thanks!

---

### Post by tgalati4 on 2013-07-15
I don't think there is a way to do that.  A user is either allowed to print or not print to a printer.  If allowed to print (authenticated user and password), then that user can change the print job options from the default values.  Later on, in the same application, those options generally become "sticky"--most likely stored in the user's configuration file for a given application.

What is the specific use case that you are trying to address?  

Perhaps you need to write some scripts to run on individual (client) machines to clear any custom print settings.  This sounds like an 80/20 problem.  80% of the problem is caused by 20% of the users, so working with those users directly might help the situation.

CUPs has a robust policy implementation ([http://www.cups.org/documentation.php/doc-1.7/policies.html](http://www.cups.org/documentation.php/doc-1.7/policies.html)), but it does not have the ability to limit job settings if you are allowed to print.  Some business printers have settings in the control panel that limit what is published to the network for options--you might explore that route.

Otherwise, I would write a *notify-send* script that gently reminds users of the preferred job settings for a given printer every time a job is submitted to that printer.  That feature is something CUPs does quite well--pre and post print commands.

```
notify-send -i printer-symbolic REMINDER "Please set the Color Printer back to Single-Sided when finished.  Thanks."
```

---

### Post by etherape88 on 2013-07-16
Hi tgalati4,

Thanks for your answer i will dive deeper in the cups policy documentation maybe there is no out of the box solution but anything that can help further is welcome.

---

