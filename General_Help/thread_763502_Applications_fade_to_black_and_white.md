---
title: "Applications fade to black and white"
date: 2008-04-23
forum: General Help
---

### Post by Dan Sarf on 2008-04-23
Hello

I am a newbie Ubuntu user. The problem I'm having is that quite regularly the application which I am using will freeze for a few moments and the window will "fade" to black and white during the freeze.  I can usually switch to another app during the freeze but if I do, the second app often freezes too.

I thought it might have something to do with processor power but it even happens if I am only in one app.

Any tips much appreciated!

DS

---

### Post by chrisccoulson on 2008-04-23
If you're using Compiz, an application will fade to black and white to signal that the application is not responding. This usually occurs if an application has crashed, but I find sometimes it happens to an application if I have another application causing heavy disk I/O.

Which apps are you seeing this with? Is there a lot of hard disk activity when it happens?

---

### Post by Dan Sarf on 2008-04-23
I don't even know what Compiz is - I am only using it if it is part of the standard installation!

This seems to happen at random - not just when I am doing anything intensive.  It happens in all applications eg Firefox, Pidgin.  I have quite a good computer and I don't use it for much strenuous processing so I can't see how it could be because I am pushing it to its limits...

DS

---

### Post by ryanhaigh on 2008-04-23
Do you have desktop effects enabled in system>preferences>appearance, if so you are using Compiz, which is what allows you to have all the fancy effects. Compiz indeed uses this greying out to indicate the the window/application is unresponsive, this happens to me all the time when using firefox and these very forums although others have mentioned that it happens when watching something using flash, like a youtube video. Pidgin has also done it to me a couple of times when the msn protocol refused to connect and was for some reason using all my cpu. A lot of the time you can just go about your work and wait for the application to come back, if the problem is persistent you can hit close a few times and compiz will offer to force the application to quit. Also you may check whether a 'freezing' app is using all your cpu by using the sytem monitor in system>admin or top in the commandline.

---

### Post by Dan Sarf on 2008-04-23
OK brilliant thanks for both your advice. I will try disabling the special effects.

---

### Post by ryanhaigh on 2008-04-23
> **Dan Sarf said:**
> OK brilliant thanks for both your advice. I will try disabling the special effects.

Disabling the effects will have...well no effect, the windows will still likely be unresponsive you just won't get the visual letting you know they have stopped responding.

---

### Post by Dan Sarf on 2008-04-23
I can't work out why Firefox would freeze so regularly when it used to be absolutely fine under Windows!

---

### Post by ryanhaigh on 2008-04-23
> **Dan Sarf said:**
> I can't work out why Firefox would freeze so regularly when it used to be absolutely fine under Windows!

You and me both...not to mention the countless others who have these issues. I haven't tried the beta of FF3 extensively but in the time I used it this was not an issue.

---

### Post by chrisccoulson on 2008-04-23
Freezes with Firefox seem to be very common, especially with the Adobe Flash plugin.

---

### Post by Papa_Smurf on 2009-09-27
If Jack control locks up (which happens often to us new users if we do things out of sequence) all three windows have the Close option grayed out. clicking it a few times does not alert the Compiz desktop effects to give us the option to close out an unresponsive application. How else can newbs force a shutdown of crashed/locked apps?:confused:

Answer: (reading from the [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065) Handbook): Use the System->Administration->System Monitor applet, in the Processes tab, select the process and click End Process. Very similar to windoze.

---

### Post by ryanhaigh on 2009-09-27
Alt-F2 will bring up the run dialog. Enter the command ```
xkill
``` and then click the non-responsive window.

---

