---
title: "Browser Hijacking"
date: 2014-04-21
forum: General Help
---

### Post by abacki on 2014-04-21
Hi everyone. I hope this isn't considered a chronic post, but, has anyone else had this problem: This link is just one of several that I've come across. If I try to leave the link, it is only possible if I submit to a confirmation of navigation form. If I don't, I might as well shut down my browser. There has to be another solution. I see this as Bogarting, as in Bogart, of movie fame.  Any suggestions, comments?

Ubuntu 12.04


[http://www.backyardliberty.com/vsl/](http://www.backyardliberty.com/vsl/)


confirm navigation
***************************************


 WAIT! 


Would you rather read the special report, 


instead of watching the video? 


 


Click the *Stay on page* or *Cancel* button.


 to get to the text version of the presentation


*The Three Horsemen of The Coming Food Crisis* 


***************************************


Are you sure you want to leave this page?

---

### Post by bapoumba on 2014-04-21
Which browser are you using ? Please check your adons and extensions. If there is one you do not recognize, delete it.

---

### Post by Habitual on 2014-04-21
That's not hijacking, just clever coding:
```
<script>
    var split = "";
    var exit_config = [{"message":"***************************************\n\n WAIT! \n\nWould you rather read the special report, \n\ninstead of watching the video? \n\n \n\nClick the *Stay on page* or *Cancel* button.\n\n to get to the text version of the presentation\n\n*The Three Horsemen of The Coming Food Crisis* \n\n***************************************","from":"0","to":"1600000","link":"..\/tsl\/index.php","next":"1"},{"message":"***************************************\n\n WAIT! \n\n STOP...Get 40% OFF NOW! \n\nClick the *Stay on page* or *Cancel* button.\n\n to claim your voucher NOW! \n\n***************************************","from":"1600000","to":"","link":"..\/tsl\/downsell1.php","next":false}];
    var exitMessage = "***************************************\n\n WAIT! \n\nWould you rather read the special report, \n\ninstead of watching the video? \n\n \n\nClick the *Stay on page* or *Cancel* button.\n\n to get to the text version of the presentation\n\n*The Three Horsemen of The Coming Food Crisis* \n\n***************************************";
    var timetobuy = 1374000;
    var StopExit = false;
    var partialcontrol = true;
```

Use noscript.

---

### Post by abacki on 2014-04-22
> **bapoumba said:**
> Which browser are you using ? Please check your adons and extensions. If there is one you do not recognize, delete it.


Thanks bapoumba. I have no adons or extentions on either Google Chrome or Firefox. I'm assuming that you did not experience the same problem that I've complained of. I can select the cancel button, but why would someone force anyone to stay on a page?

---

### Post by bapoumba on 2014-04-22
Have you seen Habitual suggestion just above ?

In addition, please have a look at your home page and see if it's been changed.

---

### Post by abacki on 2014-04-22
> **Habitual said:**
> That's not hijacking, just clever coding:
```
<script>
    var split = "";
    var exit_config = [{"message":"***************************************\n\n WAIT! \n\nWould you rather read the special report, \n\ninstead of watching the video? \n\n \n\nClick the *Stay on page* or *Cancel* button.\n\n to get to the text version of the presentation\n\n*The Three Horsemen of The Coming Food Crisis* \n\n***************************************","from":"0","to":"1600000","link":"..\/tsl\/index.php","next":"1"},{"message":"***************************************\n\n WAIT! \n\n STOP...Get 40% OFF NOW! \n\nClick the *Stay on page* or *Cancel* button.\n\n to claim your voucher NOW! \n\n***************************************","from":"1600000","to":"","link":"..\/tsl\/downsell1.php","next":false}];
    var exitMessage = "***************************************\n\n WAIT! \n\nWould you rather read the special report, \n\ninstead of watching the video? \n\n \n\nClick the *Stay on page* or *Cancel* button.\n\n to get to the text version of the presentation\n\n*The Three Horsemen of The Coming Food Crisis* \n\n***************************************";
    var timetobuy = 1374000;
    var StopExit = false;
    var partialcontrol = true;
```

Use noscript.


Thanks Habitual.  You've mentioned 'Use noscript.'   How so?

---

### Post by CitadelUniversal on 2014-04-22
Go to Firefox addon's in the search box type noscript - you'll find several noscripts to choose from...

---

### Post by abacki on 2014-04-22
> **bapoumba said:**
> Have you seen Habitual suggestion just above ?

In addition, please have a look at your home page and see if it's been changed.



Hi bapoumba.  Google has added a new start page today, if that is what you are referring to. But, I've had no improvement concerning the problem I've mentioned.  And, Yes, I have taken note of Habitual's post. I'm not certain what is intended by [COLOR=#000000]*Use noscript.*[/COLOR]

---

### Post by bapoumba on 2014-04-22
> **abacki said:**
> Hi bapoumba.  Google has added a new start page today, if that is what you are referring to. But, I've had no improvement concerning the problem I've mentioned.  And, Yes, I have taken note of Habitual's post. I'm not certain what is intended by [COLOR=#000000]*Use noscript.*[/COLOR]

What I was meaning is that some malware change your homepage to their own. Swithcing back to google.com or other legitimate page can help remove it.

You can search for noscript extensions for either firefox or chromium/chrome and install it. It prevents all script from running on web pages. You can whiltelist the ones you are using. I find it a little invasive and some web pages do not render well at all (in particular some applications and sites I use for work).

---

### Post by abacki on 2014-04-24
I thank you all for your help.  Scriptsafe, work well enough.  Thanks, again.

---

