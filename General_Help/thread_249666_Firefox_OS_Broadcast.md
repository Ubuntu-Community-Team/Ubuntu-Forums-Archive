---
title: "Firefox OS Broadcast"
date: 2006-09-02
forum: General Help
---

### Post by tjb891 on 2006-09-02
Is there a way to keep firefox from reporting OS specific information. I understand that a website needs to know if I am using firefox or IE but is there a way to make it not report that I am using Linux and Ubuntu and the versions of the Kernel and the version of ubuntu?

---

### Post by shunthemask on 2006-09-02
If I remember correctly, the firefox user agent switcher extension lets you change whatever browser and os that is reported.  Check it out:
[https://addons.mozilla.org/firefox/59/]("https://addons.mozilla.org/firefox/59/")
I don't recall if it lets you return no os info or not, tho.

---

### Post by Grog140 on 2006-09-02
I haven't used it but there is an extension I have heard of that does this.

I think it was call TrackMeNot.

---

### Post by x64Jimbo on 2006-09-02
> **shunthemask said:**
> If I remember correctly, the firefox user agent switcher extension lets you change whatever browser and os that is reported.  Check it out:
[https://addons.mozilla.org/firefox/59/]("https://addons.mozilla.org/firefox/59/")
I don't recall if it lets you return no os info or not, tho.
The nice thing about that extension is that you can masquerade as Windows & IE 6 right out of the box. This is quite helpful when visiting websites that are administered by MS zealots that won't let you view anything unless you're using a "supported browser"

---

### Post by tjb891 on 2006-09-03
> **shunthemask said:**
> If I remember correctly, the firefox user agent switcher extension lets you change whatever browser and os that is reported.  Check it out:
[https://addons.mozilla.org/firefox/59/]("https://addons.mozilla.org/firefox/59/")
I don't recall if it lets you return no os info or not, tho.

Thankyou, it does change the OS. But unfortunately it really does nothing for  
anonomity. 
Information without User Switcher Agent 
 Browser User Agent:
	M**ozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060731 Ubuntu/dapper-security Firefox/1.5.0.5**

Information with User Switcher Agent 
  	**Opera/8.51 (Windows NT 5.1; U; en)**

So it seems to work, unfortunately under browser plugins it gives this information
[B]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
 nphelix.so
 	Shockwave Flash
 libflashplayer.so
 
Google VLC multimedia plugin 1.0
 mplayerplug-in-gmp.so
 	QuickTime Plug-in 6.0
 mplayerplug-in-qt.so
 
RealPlayer 9
 mplayerplug-in-rm.so
 	Windows Media Player Plugin
 mplayerplug-in-wmp.so
 
mplayerplug-in 3.17
 mplayerplug-in.so
 	Java(TM) Plug-in 1.5.0_06-b05
 libjavaplugin_oji.so[/B]

so they still know you are hiding. But many websites probably don't log multimedia inforation.

---

### Post by x64Jimbo on 2006-09-04
If you want anonymity, you should be using a proxy server.

---

### Post by tjb891 on 2006-09-04
good point

---

